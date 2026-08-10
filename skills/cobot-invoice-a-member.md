---
name: cobot-invoice-a-member
description: >-
  Add a charge to a Cobot membership, issue and lock the invoice, retrieve the PDF, send a
  reminder, and record a payment — the money path of a coworking space.
generated: '2026-08-09'
method: generated
source: openapi/cobot-api2-openapi.yml (operationIds verified against the spec)
api: https://api.cobot.me
spec: openapi/cobot-api2-openapi.yml
operations:
  - get-space-memberships
  - get-membership
  - create-invoice-charges
  - post-invoices
  - get-invoice
  - lock-invoice
  - get-invoice-pdf
  - create-invoice-reminder
  - create-payment
scopes:
  - read_memberships
  - read_invoices
  - write_invoices
  - write_invoice_reminders
  - write_payments
---

# Invoice a member in Cobot

JSON:API rules apply throughout: `Accept: application/vnd.api+json` on every request,
`Content-Type: application/vnd.api+json` on every non-GET, `Authorization: bearer <token>`.

**Read this before you write anything:** Cobot exposes **no idempotency key**. `POST
/invoice_charges`, `POST /invoices`, `POST /payments` and `POST /refunds` are all
non-idempotent creates. Every retry in this flow must be preceded by a read.

## 1. Find the membership

- `get-space-memberships` — `GET /spaces/{spaceId}/memberships` (scope `read_memberships`)
- `get-membership` — `GET /memberships/{id}` (scope `read_memberships`)

Collections paginate with `page[number]` / `page[size]` (default 72, max 200).

## 2. Add the charges

- `create-invoice-charges` — `POST /invoice_charges` (scope `write_invoices`)

Charges accumulate against the membership and land on its next invoice. Money values follow the
spec's `money` / `decimal` schemas — decimals are transported as **strings** matching
`^-?\d+(\.\d+)?$`, never as floats. Do not round-trip them through a binary float.

## 3. Issue the invoice

- `post-invoices` — `POST /invoices` (scope `write_invoices`)
- `get-invoice` — `GET /invoices/{id}` (scope `read_invoices`)

If this returns `422`, the invoice failed because of missing or invalid data — read
`errors[].source.pointer` to find which attribute. If it returns `404`, the space has no Stripe
payment method configured or has no subscription yet (still in trial); that is a space-setup
problem, not a request problem.

## 4. Lock it, then fetch the PDF

- `lock-invoice` — `POST /invoices/{id}/lock` (scope `write_invoices`)
- `get-invoice-pdf` — `GET /invoices/{id}.pdf` (scope `read_invoices`)

Locking is the point of no return: once an invoice has an e-invoice or a final PDF attached,
`unlock-invoice` returns `409` and the document cannot be unlocked. Lock only after the numbers
are final.

## 5. Chase and settle

- `create-invoice-reminder` — `POST /invoice_reminders` (scope `write_invoice_reminders`)
- `create-payment` — `POST /payments` (scope `write_payments`)

`create-payment` returns `422` when capture fails or the space's Stripe setup is wrong — the
`detail` string is written for a human operator, so surface it rather than swallowing it. Cobot
does not process cards itself; it delegates to Stripe, PayPal, GoCardless, Adyen, Fidelity ACH or
Authorize.net depending on how the space is configured.

## 6. Watch for the outcome instead of polling

The invoice lifecycle is covered by webhook events on the **legacy v1 API** (API 2 declares no
webhooks): `created_invoice`, `updated_invoice`, `sent_invoice`, `wrote_off_invoice`,
`requested_e_invoice`, `deleted_invoice`. Subscribe via
`POST https://<subdomain>.cobot.me/api/subscriptions` with scope `write_subscriptions`.
Payloads carry only a resource URL, so re-fetch with your own token — there is no payload
signature to verify.

## Error map

| Status | Meaning in this flow |
|---|---|
| `402` | The operation touches a paid add-on the space has not purchased (all 13 declared 402s are the external-resources add-on) |
| `404` | Missing Stripe payment method, or the space has no subscription yet |
| `409` | Invoice has an e-invoice or final PDF and cannot be unlocked |
| `422` | Validation failure, or the payment capture / refund failed downstream |
| `429` | 60 req/min/user exceeded — honor `Retry-After` |

## Related artifacts

- `errors/cobot-problem-types.yml`
- `conventions/cobot-conventions.yml`
- `data-model/cobot-data-model.yml` — how invoices relate to memberships, spaces and contacts
