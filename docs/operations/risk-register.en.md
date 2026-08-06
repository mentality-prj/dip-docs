# Risk Register

Language: [Українська (default)](risk-register.md) | English

## Purpose

A live risk register for monthly updates (not a narrative document).

| Risk ID | Category         | Description                                               | Probability | Impact | Detection Method                                    | Trigger                                                   | Mitigation                                                 | Contingency Plan                                                     | Owner           | Status | Review Date |
| ------- | ---------------- | --------------------------------------------------------- | ----------- | ------ | --------------------------------------------------- | --------------------------------------------------------- | ---------------------------------------------------------- | -------------------------------------------------------------------- | --------------- | ------ | ----------- |
| R-001   | Scientific       | Hypotheses fail to show statistically significant effect. | Medium      | High   | Predefined statistical tests and interim analysis.  | p-value/effect size below threshold after planned sample. | Review experiment design, recalculate power.               | Narrow scope to strongest hypothesis and rerun with adjusted sample. | Scientific Lead | Open   | 2026-09-01  |
| R-002   | Data Quality     | Insufficient coverage/completeness for key features.      | Medium      | High   | Data quality dashboard and missingness diagnostics. | Coverage below threshold or repeated null spikes.         | Quality gates, missingness diagnostics, fallback policy.   | Freeze affected features and switch to conservative baseline.        | Data Lead       | Open   | 2026-09-01  |
| R-003   | Technical        | Latency degradation in online decision flows.             | Medium      | Medium | Performance monitoring and load benchmarks.         | p95 latency exceeds budget for 3 consecutive checks.      | Profiling, caching, SLO alerts, performance budget.        | Disable non-critical diagnostics and reduce payload size.            | Platform Lead   | Open   | 2026-09-01  |
| R-004   | Compliance       | GDPR non-conformant data handling in pilot operations.    | Low         | High   | Compliance audit and DSAR/SOP checks.               | Audit finding or non-compliant access event.              | DPIA, SOP enforcement, access audits.                      | Halt affected processing and initiate incident response.             | DPO             | Open   | 2026-09-01  |
| R-005   | Adoption         | Low recommendation adoption among B2B users.              | Medium      | Medium | Adoption analytics and user feedback.               | Response/adoption rate below target for 2 cycles.         | UX iterations, explainability tuning, onboarding playbook. | Simplify recommendation format and add guided workflows.             | Product Lead    | Open   | 2026-09-01  |
| R-006   | Model Governance | Drift causes unstable policy decisions.                   | Medium      | High   | Drift monitoring and policy health checks.          | Drift or trust score crosses degraded threshold.          | Trust gating, auto-mitigation, rollback triggers.          | Force rules-only mode until health recovers.                         | ML Lead         | Open   | 2026-09-01  |

## Horizon Europe References

- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
