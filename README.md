# Blend (blend-mortgage)

Blend (Blend Labs) is a cloud digital-lending and account-opening platform for banks, credit unions, and mortgage lenders. Its Builder platform powers consumer-facing origination for mortgage (home lending), consumer lending (home equity, personal loans, credit cards, auto), and deposit account opening. The Blend Public API is a documented REST surface at [developers.blend.com](https://developers.blend.com/blend) (current version v12.0.0) that lets lenders and certified technology partners create and manage lending applications, borrowers/parties, documents and disclosures, pricing, closings and eSignature packages, follow-ups (tasks), lenders and assignments, and webhook event notifications, and export industry-standard loan files (Fannie Mae 3.2, MISMO 3.3.1/3.4) into a loan origination system (LOS).

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/blend-mortgage/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/blend-mortgage/refs/heads/main/apis.yml)

## Access Model (Important)

Blend's API is **documented publicly but access is credential-gated**. There is no open, self-service, credit-card signup for API keys. Tokens are issued to:

- **Blend customers** (banks, credit unions, mortgage lenders) as an entitlement of their platform subscription - contact your Blend account team.
- **Certified integration partners** (LOS, POS, CRM, verification, title/closing, and AI-agent integrators) - contact Blend partnerships to build and certify against the Public API in a beta/integration environment.

Authentication uses an `authorization: BEARER {token}` header, plus a `blend-api-version` header (to pin the API version) and a `blend-target-instance` header in the form `tenant~instance`. API Secret Keys (base64-encoded 80-byte secrets) are exchanged for short-lived, request-scoped JWTs at Blend's API Gateway; IP allowlisting and rate limiting are supported.

Blend has also shipped an **MCP server** exposing the lending platform to AI agents, using least-privilege Lending API credentials and enabled per account in a beta environment.

> **endpointsModeled:** The paths, methods, and resource names in this entry (apis.yml, OpenAPI, and collections) are modeled from Blend's public developer documentation and reference - the developers.blend.com `llms.txt` endpoint index, Quick Start Guide, LOS Guide, API auth/security details, and the create/export home-loan guides. Individual request/response field schemas are representative rather than field-complete, because Blend's authoritative machine-readable spec (developers.blend.com/blend/openapi) is behind credentialed access.

## Tags

- Digital Lending
- Mortgage
- Consumer Lending
- Account Opening
- FinTech
- Loan Origination
- Banking
- Financial Services

## Timestamps

- **Created:** 2026-07-04
- **Modified:** 2026-07-04

## APIs

### Blend Home Lending Applications API

Create, list, retrieve, update, and delete home lending (mortgage) applications. Manage LOS milestones, decisions, intent-to-proceed, underwriting results, activities, and lender takeover. The minimum to create an application is the primary borrower party name and email.

- **Human URL:** [https://developers.blend.com/blend/docs/create-a-new-home-loan](https://developers.blend.com/blend/docs/create-a-new-home-loan)
- **Base URL:** `https://api.blendlabs.com`

### Blend Borrowers & Parties API

Manage the parties (borrowers, coborrowers, realtors) on an application - add and update parties, capture eConsent, and attach party employers, other incomes, and borrower positions.

- **Human URL:** [https://developers.blend.com/blend/reference](https://developers.blend.com/blend/reference)
- **Base URL:** `https://api.blendlabs.com`

### Blend Documents & Disclosures API

Retrieve application and borrower documents, upload documents, read document metadata and export statuses, pull tax transcripts, and export the industry-standard loan application file in Fannie Mae 3.2 or MISMO 3.3.1/3.4 format for import into an LOS.

- **Human URL:** [https://developers.blend.com/blend/docs/export-a-home-loan](https://developers.blend.com/blend/docs/export-a-home-loan)
- **Base URL:** `https://api.blendlabs.com`

### Blend Products & Pricing API

Apply a priced product to a loan application, aligning the selected rate and product to the borrower's chosen loan terms.

- **Human URL:** [https://developers.blend.com/blend/reference](https://developers.blend.com/blend/reference)
- **Base URL:** `https://api.blendlabs.com`

### Blend Closings & eSignature API

Create and manage closings and eSignature packages - draft and send pre-closing and closing documents, manage eNotes, schedule Remote Online Notarization (RON) sessions, retrieve RON recordings, and issue signable document packages to borrowers.

- **Human URL:** [https://developers.blend.com/blend/reference](https://developers.blend.com/blend/reference)
- **Base URL:** `https://api.blendlabs.com`

### Blend Follow-ups (Tasks) API

Create, list, retrieve, update, and remove follow-ups (borrower tasks and conditions) on an application to request documents or actions from borrowers during the origination workflow.

- **Human URL:** [https://developers.blend.com/blend/reference](https://developers.blend.com/blend/reference)
- **Base URL:** `https://api.blendlabs.com`

### Blend Events & Webhooks API

Standard webhook event notifications (Application Submitted, Documents Submitted, Consumer Information Updated, Application Information Updated) plus a REST events surface to list events, get event descriptions, and acknowledge event status - used to drive LOS import and downstream automation.

- **Human URL:** [https://developers.blend.com/blend/docs/los-guide-how-to-integrate-with-blend](https://developers.blend.com/blend/docs/los-guide-how-to-integrate-with-blend)
- **Base URL:** `https://api.blendlabs.com`

### Blend Consumer Lending & Deposit Accounts API

Retrieve and update consumer lending applications and their documents, read account-opening applications, and list deposit account applications, products, and fundings for the banking/account-opening side of the Blend platform.

- **Human URL:** [https://developers.blend.com/blend/reference](https://developers.blend.com/blend/reference)
- **Base URL:** `https://api.blendlabs.com`

### Blend Lenders & Assignments API

Create, list, update, and remove lender users, and assign lender users (primary assignee and assignees) to applications so the right loan officers and processors own each loan.

- **Human URL:** [https://developers.blend.com/blend/reference](https://developers.blend.com/blend/reference)
- **Base URL:** `https://api.blendlabs.com`

### Blend Reporting API

Pull reporting datasets across the platform - loans, borrowers, lender users and metrics, borrower workflows/activities, follow-ups, document metadata, connectivity metrics, and NPS.

- **Human URL:** [https://developers.blend.com/blend/reference](https://developers.blend.com/blend/reference)
- **Base URL:** `https://api.blendlabs.com`

## Artifacts

- [OpenAPI](openapi/blend-mortgage-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/blend-mortgage.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/blend-mortgage.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Plans](plans/blend-mortgage-plans-pricing.yml)
- [Rate Limits](rate-limits/blend-mortgage-rate-limits.yml)
- [FinOps](finops/blend-mortgage-finops.yml)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/blendlabs-inc-)
- [Website](https://blend.com)
- [Documentation](https://developers.blend.com/blend)
- [API Reference](https://developers.blend.com/blend/reference)
- [Quick Start / Sign Up](https://developers.blend.com/blend/docs/blend-api-quick-start-guide)
- [Blog](https://blend.com/blog)
- [Plans](plans/blend-mortgage-plans-pricing.yml)
- [Rate Limits](rate-limits/blend-mortgage-rate-limits.yml)
- [Fin Ops](finops/blend-mortgage-finops.yml)

## Pricing

Blend is an enterprise SaaS lending platform. Pricing is **not published** - deals are negotiated, typically annual, and priced on loan/application volume, product mix (mortgage, consumer lending, deposit account opening, close, verification add-ons), and integration scope. Historically Blend has used per-transaction / per-funded-loan economics in parts of its mortgage business alongside platform subscription fees. The Public API is an entitlement of the customer or partner relationship rather than a separately metered, self-service product. Contact Blend sales or partnerships for current terms.

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
