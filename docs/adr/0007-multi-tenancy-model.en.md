# ADR-0007: Multi-Tenancy Model

Language: [Українська (default)](0007-multi-tenancy-model.md) | English

## Status
Accepted

## Context
DIP and Dzvin.co must isolate data and execution context across organizations and tenants.

## Options
1. Shared tenant-unaware model
2. Separate deployments per tenant
3. Tenant-scoped logical isolation on shared platform

## Decision
Tenant-scoped logical isolation on a shared platform is adopted.

## Consequences
- Access control and audit become mandatory at every decision boundary.
- Lower infrastructure duplication than full per-tenant deployments.

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
