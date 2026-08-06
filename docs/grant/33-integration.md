# Integration

## Document Metadata
- Owner: Integration Architect
- Contributors: DIP Team, Dzvin.co Team, Security Team
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Описати інтеграційну модель між Dzvin.co і DIP для стабільного та безпечного обміну decision signals.

## Integration Principles
- API-only coupling.
- No direct shared database access.
- Tenant-scoped requests.
- Contract versioning and backward compatibility.

## Core Flows
- Feature payload and context submission.
- Decision evaluation and explanation retrieval.
- Async job handling for heavy workflows.
- Diagnostics and policy telemetry integration.

## Contract Governance
- Versioned request/response schemas.
- Compatibility matrix by release.
- Deprecation policy with migration windows.

## Security Requirements
- AuthN/AuthZ per surface.
- Scoped API keys/tokens.
- Request integrity and audit logging.

## Reliability Requirements
- Timeout/retry policy.
- Idempotency for critical operations.
- Fallback behavior on DIP unavailability.

## Acceptance Criteria
- Integration contract formally documented and tested.
- Failure modes covered by fallback and alerting.
- Compatibility checks part of release gates.

## Links
- Related docs: 34-api.md, 35-security.md, 15-dip-architecture.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
