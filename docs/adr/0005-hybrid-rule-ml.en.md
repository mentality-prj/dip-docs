# ADR-0005: Hybrid Rule+ML Decision Policy

Language: [Українська (default)](0005-hybrid-rule-ml.md) | English

## Status
Accepted

## Context
Rules-only is not flexible enough, and ML-only is not transparent enough for a sensitive domain.

## Options
1. Rules-only
2. ML-only
3. Hybrid rule+ML with policy governance

## Decision
A hybrid rule+ML approach with a trust-gated policy layer is selected.

## Consequences
- Pros: better balance of interpretability, quality, and safety.
- Cons: higher complexity for evaluation and runtime governance.

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
