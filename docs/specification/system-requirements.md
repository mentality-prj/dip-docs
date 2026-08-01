# System Requirements Specification (SRS)

## Purpose
Єдиний реєстр вимог для DIP + Dzvin.co. Усі Work Packages, deliverables і acceptance criteria повинні посилатися на ID вимог із цього документа.

## Scope
- DIP platform core
- Dzvin.co integration and product surfaces
- Research-to-production governance

## Functional Requirements

| ID | Requirement | Rationale | Verification Method | Linked Docs |
|----|-------------|-----------|---------------------|-------------|
| FR-001 | Система повинна виконувати decision workflows на основі rule+ML policy. | Core product value. | Integration tests + evaluation report. | docs/grant/16-decision-engine.md |
| FR-002 | Система повинна повертати explainability payload для кожного high-impact рішення. | Trust and governance. | Contract tests + XAI validation. | docs/grant/20-explainability.md |
| FR-003 | Система повинна підтримувати sync/async decision execution. | Operational scalability. | API tests + latency monitoring. | docs/grant/34-api.md |
| FR-004 | Система повинна забезпечувати tenant-scoped access control для всіх чутливих API. | Security and compliance. | Security tests + audit review. | docs/grant/35-security.md |
| FR-005 | Система повинна зберігати auditable decision traces для відтворюваності. | Research evidence and compliance. | Audit sampling + reproducibility replay. | docs/grant/30-reproducibility.md |
| FR-006 | Система повинна підтримувати керовані policy overrides з журналом змін. | Safe operations under drift. | Governance tests + override audit logs. | docs/grant/16-decision-engine.md |
| FR-007 | Система повинна підтримувати versioned feature and model compatibility matrix. | Prevent train-serve mismatch. | Registry checks + release gates. | docs/grant/17-feature-store.md, docs/grant/18-model-registry.md |
| FR-008 | Система повинна надавати admin diagnostics для policy/model health. | Runtime quality control. | Diagnostics endpoint checks. | docs/grant/25-evaluation.md |

## Non-Functional Requirements

| ID | Requirement | Target | Verification Method | Linked Docs |
|----|-------------|--------|---------------------|-------------|
| NFR-001 | Latency (online feature retrieval p95). | < 150 ms | Performance tests + monitoring. | docs/research/03-wp-success-criteria.md |
| NFR-002 | API availability in pilot phase. | >= 99.5% | SLO monitoring. | docs/grant/34-api.md |
| NFR-003 | Decision trace completeness. | 100% for mandatory flows | Audit reports. | docs/grant/16-decision-engine.md |
| NFR-004 | Explainability comprehension. | >= 80% correct interpretation | User validation study. | docs/grant/29-explainability-validation.md |
| NFR-005 | Trust uplift with explanations. | >= +10% vs baseline | Controlled experiment. | docs/research/03-wp-success-criteria.md |
| NFR-006 | Security incident tolerance. | 0 unresolved critical incidents | Security governance review. | docs/grant/35-security.md |
| NFR-007 | Reproducibility for key claims. | 100% reproducibility certificates for top claims | Reproduction protocol audit. | docs/grant/30-reproducibility.md |
| NFR-008 | Compliance response SLA (data subject requests). | Defined SOP and tracked SLA | GDPR operations audit. | docs/grant/36-gdpr.md |

## Traceability Rule
- Кожен deliverable у `docs/operations/deliverables-register.md` повинен посилатися мінімум на 1 FR або NFR.
- Кожен WP acceptance criteria у `docs/research/03-wp-success-criteria.md` має бути мапований на вимоги цього SRS.
