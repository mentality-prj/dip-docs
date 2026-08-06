# ADR-0002: MongoDB for Flexible Domain and Event Data

Language: [Українська (default)](0002-mongodb.md) | English

## Status
Accepted

## Context
Flexible schemas are needed for workflows, decision artifacts, and audit/event records.

## Options
1. MongoDB
2. Relational-only approach
3. Hybrid polyglot storage from day one

## Decision
MongoDB is used as the primary operational store at the current stage.

## Consequences
- Pros: schema flexibility, faster domain model iteration.
- Cons: requires strict governance for consistency and indexing.

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
