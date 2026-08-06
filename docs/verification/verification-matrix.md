# Verification Matrix

## Purpose

Матриця зв'язку Requirement -> Test method -> Evidence -> Status.

| Requirement | Test method                   | Evidence                      | Status  | Owner               | Notes                              |
| ----------- | ----------------------------- | ----------------------------- | ------- | ------------------- | ---------------------------------- |
| FR-001      | API test + evaluation report  | test_decision.py, eval report | Done    | Platform Lead       | Hybrid decision execution          |
| FR-002      | Integration test + XAI report | explanation report            | Partial | Explainability Lead | Need stronger user-study evidence  |
| FR-003      | API test + load test          | api latency benchmark         | Done    | API Lead            | Sync/async execution verified      |
| FR-004      | Security test                 | auth/audit test results       | Done    | Security Lead       | Tenant-scoped access verified      |
| FR-005      | Reproducibility replay        | replay log + certificate      | Partial | Research Lead       | Add more pilot-derived evidence    |
| FR-006      | Governance test               | policy override audit         | Done    | ML Lead             | Override logging verified          |
| FR-007      | Registry check + release gate | compatibility matrix          | Partial | Data Platform Lead  | Needs full model registry coverage |
| FR-008      | Diagnostics endpoint test     | diagnostics test output       | Done    | Evaluation Lead     | Admin diagnostics available        |
| NFR-001     | Benchmark                     | benchmark-2026-Q3             | Pending | Platform Lead       | Target <150 ms p95                 |
| NFR-002     | SLO monitoring                | uptime report                 | Pending | API Lead            | Pilot phase monitoring required    |
| NFR-003     | Audit report                  | trace completeness audit      | Done    | Research Lead       | Mandatory flows only               |
| NFR-004     | User validation study         | comprehension report          | Partial | UX Research Lead    | Increase sample size               |
| NFR-005     | Controlled experiment         | trust uplift report           | Pending | Research Lead       | Await pilot data                   |
| NFR-006     | Security review               | incident review log           | Done    | Security Lead       | No unresolved critical incidents   |
| NFR-007     | Reproduction audit            | reproducibility certificate   | Pending | Repro Lead          | Need top-claim certificates        |
| NFR-008     | GDPR audit                    | DSAR/SOP evidence             | Done    | DPO                 | SOP documented                     |

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
