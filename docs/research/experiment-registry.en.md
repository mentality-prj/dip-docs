# Experiment Registry

Language: [Українська (default)](experiment-registry.md) | English

## Purpose

Catalog all actual experiments, from baseline studies to hybrid policy validation, user validation, and pilot studies.

## Registry Rules

- Each experiment must have a unique ID.
- Each record must reference the traceability matrix.
- Statuses: Planned, Running, Completed, Failed, Inconclusive.

| ID      | Goal                        | Dataset      | Model/Policy        | Result  | Status  | Linked RQ | Evidence                                   | Owner                 |
| ------- | --------------------------- | ------------ | ------------------- | ------- | ------- | --------- | ------------------------------------------ | --------------------- |
| EXP-001 | Baseline risk prediction    | Cohort v1    | Logistic Regression | Pending | Planned | RQ1       | docs/research/01-traceability-matrix.en.md | ML Lead               |
| EXP-002 | Hybrid DIP decision policy  | Cohort v2    | Rules + RF          | Pending | Planned | RQ2       | docs/research/01-traceability-matrix.en.md | Decision Science Lead |
| EXP-003 | Explainability trust study  | Pilot users  | XAI templates       | Pending | Planned | RQ3       | docs/research/01-traceability-matrix.en.md | UX Research Lead      |
| EXP-004 | Adaptive baseline stability | Cohort v2    | Adaptive baseline   | Pending | Planned | RQ4       | docs/research/01-traceability-matrix.en.md | ML Lead               |
| EXP-005 | Governance mitigation       | Pilot stream | Policy control      | Pending | Planned | RQ5       | docs/research/01-traceability-matrix.en.md | Platform Lead         |

## Horizon Europe References

- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
