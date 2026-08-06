# System Requirements Specification (SRS)

Language: [Українська (default)](system-requirements.md) | English

## Purpose

A single requirements register for DIP + Dzvin.co. All Work Packages, deliverables, and acceptance criteria must reference requirement IDs from this document.

## Scope

- DIP platform core
- Dzvin.co integration and product surfaces
- Research-to-production governance

## Functional Requirements

| ID     | Requirement                                                                       | Priority | Owner                 | Acceptance Criteria                                                                        | Verification Method                      | Linked Docs                                                     |
| ------ | --------------------------------------------------------------------------------- | -------- | --------------------- | ------------------------------------------------------------------------------------------ | ---------------------------------------- | --------------------------------------------------------------- |
| FR-001 | The system shall execute decision workflows using a hybrid rule+ML policy.        | High     | Decision Science Lead | Decision engine returns decision, actions, confidence, and trace for valid workflow input. | Integration tests + evaluation report.   | docs/grant/16-decision-engine.md                                |
| FR-002 | The system shall return an explainability payload for every high-impact decision. | High     | Explainability Lead   | Response includes executed rules, feature evidence, and confidence context.                | Contract tests + XAI validation.         | docs/grant/20-explainability.md                                 |
| FR-003 | The system shall support both sync and async decision execution modes.            | Medium   | API Lead              | Both modes are available and produce equivalent functional output.                         | API tests + latency monitoring.          | docs/grant/34-api.md                                            |
| FR-004 | The system shall enforce tenant-scoped access control for all sensitive APIs.     | High     | Security Lead         | Cross-tenant access is blocked and audited.                                                | Security tests + audit review.           | docs/grant/35-security.md                                       |
| FR-005 | The system shall persist auditable decision traces for reproducibility.           | High     | Research Lead         | Trace can be replayed from stored inputs, policy version, and output artifacts.            | Audit sampling + reproducibility replay. | docs/grant/30-reproducibility.md                                |
| FR-006 | The system shall support governed policy overrides with change logging.           | Medium   | ML Lead               | Every override has owner, reason, TTL, and an audit entry.                                 | Governance tests + override audit logs.  | docs/grant/16-decision-engine.md                                |
| FR-007 | The system shall maintain versioned feature-model compatibility matrix.           | High     | Data Platform Lead    | Feature/model versions are linked and release-gated.                                       | Registry checks + release gates.         | docs/grant/17-feature-store.md, docs/grant/18-model-registry.md |
| FR-008 | The system shall expose admin diagnostics for policy/model health.                | Medium   | Evaluation Lead       | Admin can inspect diagnostics without exposing hidden research fields.                     | Diagnostics endpoint checks.             | docs/grant/25-evaluation.md                                     |

## Non-Functional Requirements

| ID      | Requirement                                      | Priority | Owner            | Target                                           | Verification Method             | Linked Docs                                |
| ------- | ------------------------------------------------ | -------- | ---------------- | ------------------------------------------------ | ------------------------------- | ------------------------------------------ |
| NFR-001 | Latency (online feature retrieval p95).          | High     | Platform Lead    | < 150 ms                                         | Performance tests + monitoring. | docs/research/03-wp-success-criteria.md    |
| NFR-002 | API availability in pilot phase.                 | High     | API Lead         | >= 99.5%                                         | SLO monitoring.                 | docs/grant/34-api.md                       |
| NFR-003 | Decision trace completeness.                     | High     | Research Lead    | 100% for mandatory flows                         | Audit reports.                  | docs/grant/16-decision-engine.md           |
| NFR-004 | Explainability comprehension.                    | High     | UX Research Lead | >= 80% correct interpretation                    | User validation study.          | docs/grant/29-explainability-validation.md |
| NFR-005 | Trust uplift with explanations.                  | Medium   | Research Lead    | >= +10% vs baseline                              | Controlled experiment.          | docs/research/03-wp-success-criteria.md    |
| NFR-006 | Security incident tolerance.                     | High     | Security Lead    | 0 unresolved critical incidents                  | Security governance review.     | docs/grant/35-security.md                  |
| NFR-007 | Reproducibility for key claims.                  | High     | Repro Lead       | 100% reproducibility certificates for top claims | Reproduction protocol audit.    | docs/grant/30-reproducibility.md           |
| NFR-008 | Compliance response SLA (data subject requests). | High     | DPO              | Defined SOP and tracked SLA                      | GDPR operations audit.          | docs/grant/36-gdpr.md                      |

## Traceability Rule

- Each deliverable in `docs/operations/deliverables-register.md` must reference at least one FR or NFR.
- Each WP acceptance criterion in `docs/research/03-wp-success-criteria.md` must map to this SRS.
- Each verification record in `docs/verification/verification-matrix.md` must reference one or more FR/NFR.

## Horizon Europe References

- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
