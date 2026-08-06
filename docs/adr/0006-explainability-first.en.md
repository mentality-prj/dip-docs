# ADR-0006: Explainability-First Decision Contract

Language: [Українська (default)](0006-explainability-first.md) | English

## Status
Accepted

## Context
A sensitive domain requires explanations as part of the decision, not a post-hoc UI add-on.

## Options
1. Explainability as optional UI layer
2. Explainability as diagnostics only
3. Explainability as part of core decision contract

## Decision
Explainability is part of the core decision contract.

## Consequences
- Every high-impact decision must return trace, rationale, and confidence context.
- API contract becomes richer and more suitable for audit and grant validation.

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
