# API

## Document Metadata
- Owner: API Lead
- Contributors: Platform Team, Application Team, QA
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Визначити API-контракти, версіонування і вимоги до надійності для DIP та інтеграційних поверхонь Dzvin.co.

## API Surface Classes
- Decision execution APIs
- Prediction/risk APIs
- Workflow management APIs
- Diagnostics/admin APIs

## Contract Standards
- Explicit schema definitions.
- Strong validation and typed errors.
- Stable semantic fields for downstream analytics.

## Versioning Strategy
- Major for breaking changes.
- Minor for additive changes.
- Sunset notices for deprecated versions.

## Non-Functional Requirements
- Latency SLO by endpoint class.
- Availability objectives.
- Rate limits and abuse protection.

## Security and Access
- Authenticated access only.
- Role/permission-scoped operations.
- Audit fields for sensitive calls.

## Observability
- Request IDs and trace propagation.
- Structured logs.
- Endpoint-level metrics and error taxonomy.

## Acceptance Criteria
- OpenAPI specs актуальні і покривають critical endpoints.
- Version compatibility documented.
- API quality gates включені в CI/CD.

## Links
- Related docs: 33-integration.md, 35-security.md, 15-dip-architecture.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
