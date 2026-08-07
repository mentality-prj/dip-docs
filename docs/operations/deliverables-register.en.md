# Deliverables Register

Language: [Українська (default)](deliverables-register.md) | English

## Purpose

Operational table of deliverables by work package, with owner, deadline, acceptance criteria, and dependencies.

| Deliverable ID | WP  | Deliverable                      | Owner                 | Deadline   | Acceptance Criteria                                                           | Dependencies                       | Related FR/NFR           | Status  |
| -------------- | --- | -------------------------------- | --------------------- | ---------- | ----------------------------------------------------------------------------- | ---------------------------------- | ------------------------ | ------- |
| D-2.1          | WP2 | Feature Store v1                 | Data Platform Lead    | 2026-10-15 | p95 feature retrieval <150 ms; coverage >95%; versioned metadata complete     | Dataset spec, quality gates        | FR-007, NFR-001          | Planned |
| D-3.1          | WP3 | Decision Engine Hybrid v1        | Decision Science Lead | 2026-11-15 | hybrid beats baseline on predefined metrics; mandatory decision trace enabled | Feature store, model registry      | FR-001, FR-005, NFR-003  | Planned |
| D-3.2          | WP3 | Policy Governance Controls       | ML Lead               | 2026-11-30 | mitigation/rollback triggers tested; override audit complete                  | Decision engine v1                 | FR-006, NFR-007          | Planned |
| D-4.1          | WP4 | Explainability Validation Report | Explainability Lead   | 2026-12-10 | comprehension >=80%; trust uplift >=10%; no severe safety incidents           | Decision engine, user validation   | FR-002, NFR-004, NFR-005 | Planned |
| D-5.1          | WP5 | Pilot Study Report (90 days)     | Pilot Lead            | 2027-02-01 | pilot KPI targets met; reproducibility evidence attached                      | Integration layer, policy controls | FR-003, NFR-002          | Planned |
| D-6.1          | WP6 | Impact and Exploitation Dossier  | Impact Lead           | 2027-03-01 | impact KPI evidence complete; dissemination outputs delivered                 | Pilot report, metrics reports      | FR-008                   | Planned |

## Horizon Europe References

- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
