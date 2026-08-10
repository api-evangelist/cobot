---
name: cobot-check-in-a-member
description: >-
  Check a member into a Cobot space, list who is currently on site, and check them out — the
  door/front-desk flow, and one of only two write capabilities Cobot exposes to agents through
  its own MCP server.
generated: '2026-08-09'
method: generated
source: openapi/cobot-api2-openapi.yml (operationIds verified against the spec)
api: https://api.cobot.me
spec: openapi/cobot-api2-openapi.yml
operations:
  - get-space-memberships
  - create-check-in
  - list-space-check-ins-current
  - get-membership-check-ins
  - create-check-out
scopes:
  - read_memberships
  - read_check_ins
  - write_check_ins
---

# Check a member in and out of a Cobot space

JSON:API throughout: `Accept: application/vnd.api+json`, `Content-Type: application/vnd.api+json`
on non-GETs, `Authorization: bearer <token>`.

This flow matters beyond the front desk: `read_check_ins` and `write_check_ins` are two of the
**14 scopes Cobot's own MCP server advertises** (`https://api.cobot.me/mcp`), and `write_check_ins`
is one of only **two** write scopes it exposes at all — the other being `write_bookings`. If you
are building an agent against Cobot, this is inside the sanctioned surface.

## 1. Resolve the membership

- `get-space-memberships` — `GET /spaces/{spaceId}/memberships` (scope `read_memberships`)

Use sparse fieldsets to keep the payload small — `fields[memberships]=...` — and page with
`page[number]` / `page[size]`.

## 2. Check in

- `create-check-in` — `POST /check_ins` (scope `write_check_ins`)

A `422` here means "checking in failed because a condition was not met" — for example the
membership is not active, or the member is already checked in. It is **not** retryable as-is;
read the current check-in state first (step 3) and reconcile.

There is no idempotency key on this API, so a timed-out check-in must be resolved by reading, not
by retrying.

## 3. See who is on site

- `list-space-check-ins-current` — `GET /spaces/{spaceId}/check_ins/current` (scope `read_check_ins`)
- `get-membership-check-ins` — `GET /memberships/{membershipId}/check_ins` (scope `read_check_ins`)

The first is the live occupancy view for the space; the second is one member's history.

## 4. Check out

- `create-check-out` — `PUT /check_ins/{id}/check_out` (scope `write_check_ins`)

Note the verb: check-out is a `PUT` against an existing check-in, not a `DELETE`. Because it is a
`PUT` on a specific id it is naturally safe to repeat.

## Door hardware

Cobot integrates with Kisi, Salto KS, Tapkey, Sensorberg and dormakaba Exivo. If you are wiring a
reader yourself rather than using an existing integration, Cobot documents the pattern at
<https://dev.cobot.me/page/integrating-with-access-control-systems-rfid-card-biometric-readers>
and <https://dev.cobot.me/page/access-control-system-integration>.

## Events

On the legacy v1 API the relevant webhook events are `created_checkin`, `created_checkout`,
`created_checkin_token` and `deleted_checkin_token`. See `asyncapi/cobot-webhooks.yml`.

## Related artifacts

- `mcp/cobot-mcp.yml` and `mcp/cobot-tool-crosswalk.yml` — the agent-reachable scope surface
- `conventions/cobot-conventions.yml`
- `errors/cobot-problem-types.yml`
