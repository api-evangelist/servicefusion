# Service Fusion (servicefusion)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Service Fusion is field service management (FSM) software for home-service contractors - HVAC, plumbing, electrical, appliance repair, and similar trades. It covers customer management, estimates, scheduling and dispatch, work orders/jobs, invoicing, payments, inventory, and a technician mobile app, with flat-rate pricing and unlimited users on every plan. Service Fusion exposes an Open API - a REST/JSON interface secured with OAuth 2.0 (base `https://api.servicefusion.com/v1`, token endpoint `https://api.servicefusion.com/oauth/access_token`) - that lets developers read and create records for customers, jobs, estimates, invoices, technicians, and related resources. API access is available on the Pro plan; the API is rate limited to roughly 60 requests per minute.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/servicefusion/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/servicefusion/refs/heads/main/apis.yml)

## Tags

- Field Service Management
- FSM
- Home Services
- Contractors
- Scheduling
- Dispatch
- Invoicing

## Timestamps

- **Created:** 2026-07-03
- **Modified:** 2026-07-03

## Authentication

OAuth 2.0. Register a Connected App under **My Office > Developer Settings > Connected Apps** to receive a Client ID and Client Secret, then obtain an access token from `https://api.servicefusion.com/oauth/access_token` (authorization_code or client_credentials grant) and send it as an `Authorization: Bearer` header. API access requires the **Pro** subscription tier.

> **Grounding note:** Customers, jobs, estimates, invoices, and techs are documented Service Fusion API resources. Contacts, products, services, payments, and calendar tasks are modeled from the Service Fusion FSM data model and the platform's read-and-create API conventions - verify exact paths, fields, and available methods against [https://docs.servicefusion.com/](https://docs.servicefusion.com/) before production use. In practice the public API is read-and-create heavy (list, retrieve, create); update/delete are not consistently exposed. The `/jobs` list endpoint hangs if queried without a `sort` parameter - always pass `sort=-start_date` or similar.

## APIs

### Service Fusion Customers API

List, search, retrieve, and create customer accounts - the businesses and homeowners a contractor serves - including addresses, phone/email contacts, and custom fields. Customer records anchor jobs, estimates, invoices, and payments.

- **Human URL:** [https://docs.servicefusion.com/](https://docs.servicefusion.com/)
- **Base URL:** `https://api.servicefusion.com/v1`

#### Tags

- Customers
- CRM
- Accounts

#### Properties

- [Documentation](https://docs.servicefusion.com/)
- [API Reference](https://docs.servicefusion.com/)
- [OpenAPI](openapi/servicefusion-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/servicefusion.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/servicefusion.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Service Fusion Contacts API

Manage the individual contacts and service locations attached to a customer account - names, roles, phone numbers, emails, and site addresses used for scheduling and communication.

- **Human URL:** [https://docs.servicefusion.com/](https://docs.servicefusion.com/)
- **Base URL:** `https://api.servicefusion.com/v1`

#### Tags

- Contacts
- People
- CRM

#### Properties

- [Documentation](https://docs.servicefusion.com/)
- [OpenAPI](openapi/servicefusion-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/servicefusion.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/servicefusion.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Service Fusion Jobs API

List, search, retrieve, and create jobs (work orders) - the scheduled service visits assigned to technicians. Supports filtering by status, customer, and date range. Always pass a sort parameter (e.g. `sort=-start_date`) to avoid a known hang on unsorted `/jobs` requests.

- **Human URL:** [https://docs.servicefusion.com/](https://docs.servicefusion.com/)
- **Base URL:** `https://api.servicefusion.com/v1`

#### Tags

- Jobs
- Work Orders
- Dispatch

#### Properties

- [Documentation](https://docs.servicefusion.com/)
- [API Reference](https://docs.servicefusion.com/)
- [OpenAPI](openapi/servicefusion-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/servicefusion.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/servicefusion.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Service Fusion Estimates API

List, retrieve, and create estimates (quotes) presented to customers before work begins, including line items for products and services, pricing, and status. Approved estimates convert into jobs and invoices.

- **Human URL:** [https://docs.servicefusion.com/](https://docs.servicefusion.com/)
- **Base URL:** `https://api.servicefusion.com/v1`

#### Tags

- Estimates
- Quotes
- Sales

#### Properties

- [Documentation](https://docs.servicefusion.com/)
- [API Reference](https://docs.servicefusion.com/)
- [OpenAPI](openapi/servicefusion-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/servicefusion.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/servicefusion.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Service Fusion Invoices API

List, retrieve, and create invoices billed to customers for completed work, including line items, totals, balance due, and payment status. Includes an open-invoices view for outstanding accounts receivable.

- **Human URL:** [https://docs.servicefusion.com/](https://docs.servicefusion.com/)
- **Base URL:** `https://api.servicefusion.com/v1`

#### Tags

- Invoices
- Billing
- Accounts Receivable

#### Properties

- [Documentation](https://docs.servicefusion.com/)
- [API Reference](https://docs.servicefusion.com/)
- [OpenAPI](openapi/servicefusion-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/servicefusion.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/servicefusion.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Service Fusion Products and Services API

Manage the catalog of products (inventory items and parts) and services (labor and flat-rate tasks) used as line items on estimates, jobs, and invoices, including names, descriptions, pricing, and cost.

- **Human URL:** [https://docs.servicefusion.com/](https://docs.servicefusion.com/)
- **Base URL:** `https://api.servicefusion.com/v1`

#### Tags

- Products
- Services
- Catalog

#### Properties

- [Documentation](https://docs.servicefusion.com/)
- [OpenAPI](openapi/servicefusion-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/servicefusion.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/servicefusion.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Service Fusion Payments API

List, retrieve, and record payments applied to invoices - amount, method, date, and the invoice or customer the payment settles - for reconciling accounts receivable.

- **Human URL:** [https://docs.servicefusion.com/](https://docs.servicefusion.com/)
- **Base URL:** `https://api.servicefusion.com/v1`

#### Tags

- Payments
- Transactions
- Billing

#### Properties

- [Documentation](https://docs.servicefusion.com/)
- [OpenAPI](openapi/servicefusion-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/servicefusion.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/servicefusion.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Service Fusion Techs and Users API

Retrieve the roster of technicians and users in the account - the field workforce jobs are assigned to and dispatched against - including names, contact details, and identifiers used when scheduling jobs.

- **Human URL:** [https://docs.servicefusion.com/](https://docs.servicefusion.com/)
- **Base URL:** `https://api.servicefusion.com/v1`

#### Tags

- Technicians
- Users
- Workforce

#### Properties

- [Documentation](https://docs.servicefusion.com/)
- [API Reference](https://docs.servicefusion.com/)
- [OpenAPI](openapi/servicefusion-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/servicefusion.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/servicefusion.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Service Fusion Calendar Tasks API

List, retrieve, and create calendar tasks - non-job scheduled items such as reminders, follow-ups, and internal to-dos placed on the dispatch calendar and optionally assigned to a technician or user.

- **Human URL:** [https://docs.servicefusion.com/](https://docs.servicefusion.com/)
- **Base URL:** `https://api.servicefusion.com/v1`

#### Tags

- Calendar
- Tasks
- Scheduling

#### Properties

- [Documentation](https://docs.servicefusion.com/)
- [OpenAPI](openapi/servicefusion-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/servicefusion.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/servicefusion.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/service-fusion)
- [Website](https://www.servicefusion.com)
- [Documentation](https://docs.servicefusion.com/)
- [Plans](plans/servicefusion-plans-pricing.yml)
- [Rate Limits](rate-limits/servicefusion-rate-limits.yml)
- [Fin Ops](finops/servicefusion-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
