# Cobot

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Cobot is coworking and flexible-workspace management software, built and operated by Upstream - Agile GmbH in Berlin, Germany. It runs the day-to-day of a coworking space or space network from one platform: memberships and plans, resource and meeting-room bookings, drop-in passes, events and ticketing, check-ins, automated invoicing and online payments, a white-label member portal and mobile app, analytics, and door access-control integrations (Kisi, Salto KS, Tapkey, Sensorberg, dormakaba Exivo). Cobot publishes a genuinely open developer surface: a 134-operation OpenAPI 3.1 contract for API 2 that follows the JSON:API standard, a legacy v1 REST API with a documented webhook event catalog, OAuth 2.0 with authorization-code + PKCE and dynamic client registration, OpenID Connect, an RFC 9727 api-catalog document, RFC 9728 protected-resource metadata, an llms.txt, and an OAuth-protected hosted MCP server at api.cobot.me/mcp.

**Areas:** Company · Co-Working · Workspace Management · Space Management · Real Estate · Booking · Reservations · Membership · Invoicing · Payments · Event · Access Control

## Cobot on APIs.io

Everything profiled for Cobot is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/cobot/](https://apis.io/providers/cobot/)** — or go straight to one of the APIs or properties below.

### APIs (44)

- [Cobot API v1 (legacy)](https://apis.io/apis/cobot/cobot-api-v1/) — The original Cobot REST API, still available and still the only surface that carries the webhook subscription API. Documented per-resource on…
- [Cobot MCP Server](https://apis.io/apis/cobot/cobot-mcp/) — A hosted, remote Model Context Protocol server operated by Cobot at api.cobot.me/mcp. It is live and OAuth 2.0 protected — an anonymous tools/list returns…
- [Cobot Allocation API](https://apis.io/apis/cobot/cobot-allocation-api/) — A long-term allocation of a resource to a membership or team.
- [Cobot Approval API](https://apis.io/apis/cobot/cobot-approval-api/) — Approving terms & conditions, privacy policies etc. as a member of a space.
- [Cobot Article API](https://apis.io/apis/cobot/cobot-article-api/) — A help desk article explaning an aspect of the space.
- [Cobot Booking API](https://apis.io/apis/cobot/cobot-booking-api/) — A booking of a resource in the booking calendar.
- [Cobot Booking Credit API](https://apis.io/apis/cobot/cobot-booking-credit-api/) — Booking credits are added to plans and give memberships free booking time or a fixed amount of free bookings. The hourly rate of a resource can also be…
- [Cobot Built-in Email Customizations API](https://apis.io/apis/cobot/cobot-built-in-email-customizations-api/) — Email customizations for emails that can be sent via Cobot.
- [Cobot Calendar Blocker API](https://apis.io/apis/cobot/cobot-calendar-blocker-api/) — Blocks off a space for member/external bookings and drop-in passes.
- [Cobot Check In API](https://apis.io/apis/cobot/cobot-check-in-api/) — Members check in to a space for attendance tracking and for using up their time passes.
- [Cobot Contact API](https://apis.io/apis/cobot/cobot-contact-api/) — Non-member contacts a space has.
- [Cobot Cost Center API](https://apis.io/apis/cobot/cobot-cost-center-api/) — Cost centers are used to categorize invoice items. Anything that can be invoiced can be assigned a cost center. When a service/charge is added to an…
- [Cobot Customer API](https://apis.io/apis/cobot/cobot-customer-api/) — A trial space can be converted to a customer
- [Cobot Discount Code API](https://apis.io/apis/cobot/cobot-discount-code-api/) — A discount code can be used to offer a discount for various products in a space.
- [Cobot Drop-In Pass API](https://apis.io/apis/cobot/cobot-drop-in-pass-api/) — Purchased drop-in passes.
- [Cobot Drop-In Pass Purchase API](https://apis.io/apis/cobot/cobot-drop-in-pass-purchase-api/) — A purchase of drop-in-passes, currently only supports buying one pass at a time.
- [Cobot Drop-In Pass Template API](https://apis.io/apis/cobot/cobot-drop-in-pass-template-api/) — Drop-in pass templates are templates for drop-in passes that can be bought by visitors.
- [Cobot Event API](https://apis.io/apis/cobot/cobot-event-api/) — Spaces can run events for their members or the public. Events are created and later published by admins, at which point members are able to see and attend…
- [Cobot External Booking API](https://apis.io/apis/cobot/cobot-external-booking-api/) — After a resource has been enabled for external booking (see _External Resource_) it can be booked by visitors (non-members) using external booking…
- [Cobot External Resource API](https://apis.io/apis/cobot/cobot-external-resource-api/) — A space's resources can be enabled for external booking, which means they can be booked by guests without a Cobot account or space membership. All resources…
- [Cobot Invoice API](https://apis.io/apis/cobot/cobot-invoice-api/) — Invoices are automatically generated once a month, based on members' activity. In addition, manual invoices can be generated at any time.
- [Cobot Invoice Reminder API](https://apis.io/apis/cobot/cobot-invoice-reminder-api/) — Admins can send invoice reminders for overdue invoices.
- [Cobot Membership API](https://apis.io/apis/cobot/cobot-membership-api/) — Represents a person being a member in a space. Can optionally be connected to a User.
- [Cobot Membership Plan API](https://apis.io/apis/cobot/cobot-membership-plan-api/) — The plans belonging to a membership. When a membership is signed up one of the space's plans is selected and a copy is created for the membership. A…
- [Cobot Membership Profile API](https://apis.io/apis/cobot/cobot-membership-profile-api/) — Social profile for a membership.
- [Cobot Navigation Link API](https://apis.io/apis/cobot/cobot-navigation-link-api/) — Navigation links allow you to embed 3rd party apps on a space's Cobot UI. See also the single page app endpoints.
- [Cobot Network API](https://apis.io/apis/cobot/cobot-network-api/) — Multiple spaces can form a network. This allows their members to access multiple spaces, for example to book resources.
- [Cobot Payment API](https://apis.io/apis/cobot/cobot-payment-api/) — *The payment API is in development. Endpoints may be missing or not working yet.* Payments allow any user (i.e. non-members) to pay for items on Cobot via…
- [Cobot Payment Method API](https://apis.io/apis/cobot/cobot-payment-method-api/) — Spaces can set up payment methods that members can use to make payments to the space. Payment methods can be automated via a payment provider such as Stripe…
- [Cobot Product API](https://apis.io/apis/cobot/cobot-product-api/) — Products can be set up by a space and then used as booking extras or to create charges from. Examples are coffee, projectors, additional cleaning services etc.
- [Cobot Refund API](https://apis.io/apis/cobot/cobot-refund-api/) — A full or partial refund of an invoice.
- [Cobot Resource API](https://apis.io/apis/cobot/cobot-resource-api/) — A resource can be booked on an hourly basis using the booking calendar. Examples are conference rooms, presentation equipment, bikes etc.
- [Cobot Revenue Account API](https://apis.io/apis/cobot/cobot-revenue-account-api/) — Revenue accounts are used to categorize invoice items. Anything that can be invoiced can be assigned a revenue account. When a service/charge is added to an…
- [Cobot Single page app API](https://apis.io/apis/cobot/cobot-single-page-app-api/) — A single page app consists of HTML, CSS and JavaScript code. It can be embedded into the Cobot UI via navigation links.
- [Cobot Space API](https://apis.io/apis/cobot/cobot-space-api/) — A coworking space. Spaces can form a network to allow members access to multiple spaces.
- [Cobot Space Billing Details API](https://apis.io/apis/cobot/cobot-space-billing-details-api/) — Billing details of a space.
- [Cobot Space Payment Method API](https://apis.io/apis/cobot/cobot-space-payment-method-api/) — The payment method a space uses to pay their Cobot subscription.
- [Cobot Space Preview API](https://apis.io/apis/cobot/cobot-space-preview-api/) — Preview of a to-be-created space.
- [Cobot Space Profile API](https://apis.io/apis/cobot/cobot-space-profile-api/) — Public profile information such as location, phone, website, social media links.
- [Cobot Subscription API](https://apis.io/apis/cobot/cobot-subscription-api/) — How much a space pays Cobot, how many members they can have and the extras they have booked.
- [Cobot Team API](https://apis.io/apis/cobot/cobot-team-api/) — The Team API from Cobot — 2 operation(s) for team.
- [Cobot URL API](https://apis.io/apis/cobot/cobot-url-api/) — These URLs/URL templates enable API clients to provide links to the Cobot web interface without having to hard-code them. Each Url includes a unique, never…
- [Cobot User API](https://apis.io/apis/cobot/cobot-user-api/) — A user is used to log in to Cobot via email/password. Users can be admins/members (see Membership) in multiple spaces.
- [Cobot User Email Preview API](https://apis.io/apis/cobot/cobot-user-email-preview-api/) — Confirms if a given email address is free to take.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Cobot Webhooks](https://apis.io/asyncapis/cobot/cobot-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Cobot MCP](https://apis.io/servers/cobot/cobot-mcp/)

#### Collections (40)

Postman and Open Collection request collections.

- [Cobot Allocation API](https://apis.io/collections/cobot/open-cobot-allocation-api/)
- [Cobot Approval API](https://apis.io/collections/cobot/open-cobot-approval-api/)
- [Cobot Article API](https://apis.io/collections/cobot/open-cobot-article-api/)
- [Cobot Booking API](https://apis.io/collections/cobot/open-cobot-booking-api/)
- [Cobot Booking Credit API](https://apis.io/collections/cobot/open-cobot-booking-credit-api/)
- [Cobot Built-in Email Customizations API](https://apis.io/collections/cobot/open-cobot-built-in-email-customizations-api/)
- [Cobot Calendar Blocker API](https://apis.io/collections/cobot/open-cobot-calendar-blocker-api/)
- [Cobot Check In API](https://apis.io/collections/cobot/open-cobot-check-in-api/)
- [Cobot Contact API](https://apis.io/collections/cobot/open-cobot-contact-api/)
- [Cobot Cost Center API](https://apis.io/collections/cobot/open-cobot-cost-center-api/)
- [Cobot Customer API](https://apis.io/collections/cobot/open-cobot-customer-api/)
- [Cobot Discount Code API](https://apis.io/collections/cobot/open-cobot-discount-code-api/)
- [Cobot Drop-In Pass API](https://apis.io/collections/cobot/open-cobot-drop-in-pass-api/)
- [Cobot Drop-In Pass Purchase API](https://apis.io/collections/cobot/open-cobot-drop-in-pass-purchase-api/)
- [Cobot Drop-In Pass Template API](https://apis.io/collections/cobot/open-cobot-drop-in-pass-template-api/)
- [Cobot Event API](https://apis.io/collections/cobot/open-cobot-event-api/)
- [Cobot External Booking API](https://apis.io/collections/cobot/open-cobot-external-booking-api/)
- [Cobot External Resource API](https://apis.io/collections/cobot/open-cobot-external-resource-api/)
- [Cobot Invoice API](https://apis.io/collections/cobot/open-cobot-invoice-api/)
- [Cobot Invoice Reminder API](https://apis.io/collections/cobot/open-cobot-invoice-reminder-api/)
- [Cobot Membership API](https://apis.io/collections/cobot/open-cobot-membership-api/)
- [Cobot Membership Plan API](https://apis.io/collections/cobot/open-cobot-membership-plan-api/)
- [Cobot Membership Profile API](https://apis.io/collections/cobot/open-cobot-membership-profile-api/)
- [Cobot Navigation Link API](https://apis.io/collections/cobot/open-cobot-navigation-link-api/)
- [Cobot Network API](https://apis.io/collections/cobot/open-cobot-network-api/)
- …and 15 more published on APIs.io

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Cobot Api2 Overlay](https://apis.io/overlays/cobot/cobot-api2-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Cobot Authentication](https://apis.io/security/cobot/cobot-authentication/)
- [Cobot Domain Security](https://apis.io/security/cobot/cobot-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Cobot Scopes](https://apis.io/scopes/cobot/cobot-scopes/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.cobot.me/)
- [Documentation](https://dev.cobot.me/api2)
- [Getting started](https://dev.cobot.me/page/extending-cobot)
- [API reference](https://dev.cobot.me/api2)
- [Pricing](https://www.cobot.me/en/pricing)
- [Sign up](https://www.cobot.me/sign-up-space)
- [Support](https://www.cobot.me/en/support)
- [Changelog](https://www.cobot.me/pages/api_changes)
- [Blog](https://blog.cobot.me/)
- [Terms of service](https://www.cobot.me/en/terms-of-service)
- [Privacy policy](https://www.cobot.me/en/privacy-policy)
- [GitHub](https://github.com/cobot)
- [Status](https://www.cobotstatus.me/)

## API Evangelist rating

**Kin Score 51.7** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 60.6 |
| Contract governance | 18.2 |
| Operational transparency | 34.2 |
| Developer ergonomics | 66.1 |
| Access clarity | 38.2 |

**Agent readiness 58.6** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | documented (partial credit) |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | — |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | distinct |

**Regulatory alignment 34.8** — Payments

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/cobot/](https://apis.io/providers/cobot/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Cobot: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/cobot/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
