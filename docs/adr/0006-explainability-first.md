# ADR-0006: Explainability-First Decision Contract

## Status

Accepted

## Context

Чутливий домен потребує пояснень як частини рішення, а не post-hoc UI add-on.

## Options

1. Explainability as optional UI layer
2. Explainability as diagnostic only
3. Explainability as part of core decision contract

## Decision

Пояснюваність є частиною core decision contract.

## Consequences

- Кожне high-impact рішення повинно повертати trace, rationale і confidence context.
- API contract стає багатшим, але більш придатним для аудиту і грантової валідації.

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
