---
name: cobot-book-a-meeting-room
description: >-
  Find an available resource in a Cobot space network and book it for a member, pricing the
  booking before it is created so the member sees the cost first.
generated: '2026-08-09'
method: generated
source: openapi/cobot-api2-openapi.yml (operationIds verified against the spec)
api: https://api.cobot.me
spec: openapi/cobot-api2-openapi.yml
operations:
  - get-user
  - get-space
  - get-available-network-resources
  - get-network-resource-availabilities
  - post-bookings-preview
  - create-admin-booking
  - get-booking
  - update-space-booking
  - delete-space-booking
scopes:
  - read_user
  - read_spaces
  - read_resources
  - read_memberships
  - read_bookings
  - write_bookings
---

# Book a meeting room in Cobot

Cobot API 2 is a **JSON:API** service. Every request must send
`Accept: application/vnd.api+json`, every non-GET must also send
`Content-Type: application/vnd.api+json`, and authorization is
`Authorization: bearer <token>` from the OAuth 2 authorization-code flow
(`https://www.cobot.me/oauth/authorize` → `https://www.cobot.me/oauth/access_token`, PKCE `S256`).

## 1. Establish who you are and which space you are in

- `get-user` — `GET /user` (scope `read_user`). Returns the authenticated user and the
  memberships/admin roles they hold. Use sparse fieldsets to keep it small:
  `GET /user?fields[users]=email`.
- `get-space` — `GET /spaces/{spaceId}` (scope `read_spaces`).

## 2. Find something bookable

- `get-available-network-resources` — `GET /networks/{networkId}/resources/available`
  (scope `read_resources`). Ask the **network**, not the space, so multi-location spaces are
  covered in one call.
- `get-network-resource-availabilities` — `GET /networks/{networkId}/resource_availabilities`
  (scope `read_resources`) when you need the availability windows rather than just the list.

Both are collections, so JSON:API pagination applies: `page[number]`, `page[size]`
(default 72, max 200), with `meta.totalPages` and `links.next` in the response.

## 3. Price it BEFORE you create it

- `post-bookings-preview` — `POST /bookings_preview` (scopes `read_resources`, `read_memberships`).

This is the step that makes the flow safe. It returns the estimated payable price, any booking
credits that will be consumed, discounts, and taxes — without creating anything. Always show this
to the member and get confirmation before step 4.

## 4. Create the booking

- `create-admin-booking` — `POST /bookings` (scope `write_bookings`).

**There is no idempotency key on this API.** No `Idempotency-Key` header exists anywhere in the
Cobot contract. If the request times out you cannot safely blind-retry a create — instead
re-query `get-space-bookings` (`GET /spaces/{spaceId}/bookings`, scopes `read_bookings`,
`read_events`, `read_external_bookings`) for the member and time window and check whether the
booking landed before trying again.

## 5. Read, change, cancel

- `get-booking` — `GET /bookings/{id}` (scope `read_bookings`)
- `update-space-booking` — `PATCH /bookings/{id}` (scope `write_bookings`)
- `delete-space-booking` — `DELETE /bookings/{id}` (scope `write_bookings`)

## Errors you must handle

Cobot does **not** use RFC 9457 problem+json. Errors come back as a JSON:API `errors` array whose
members carry `source.pointer` (a JSON Pointer at the offending attribute) and a free-text
`detail`. There are no stable error codes — branch on the HTTP status.

| Status | What it means here | What to do |
|---|---|---|
| `400` | The resource is not bookable (4 of the 6 declared 400s in the spec say exactly this) | Pick a different resource or time; do not retry |
| `409` | The booking belongs to an event and cannot be changed or deleted through this endpoint | Re-read the booking; route the change through the event operations instead |
| `422` | Validation failed | Read `source.pointer`, fix that attribute |
| `429` | Rate limit — 60 requests/minute/user | Sleep for `Retry-After` seconds, then retry |

Note that `401`, `403`, `429` and `5xx` are **not declared** on any operation in the spec even
though every operation is scope-protected and a rate limit is documented. Handle them anyway.

## Related artifacts

- `conventions/cobot-conventions.yml` — pagination, sparse fieldsets, dates, rate limits
- `errors/cobot-problem-types.yml` — the full derived error catalog
- `scopes/cobot-scopes.yml` — all 58 OAuth scopes
- `asyncapi/cobot-webhooks.yml` — subscribe to `created_booking`, `updated_booking`,
  `booking_will_begin`, `booking_has_ended`, `deleted_booking` (legacy v1 API)
