# Service Fusion (servicefusion)

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
