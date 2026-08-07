# TRL Mapping and Evidence

Language: [Українська (default)](04-trl-mapping-evidence.md) | English

## Purpose

Show the transition Current TRL -> Target TRL -> Evidence for key components.

## TRL Table

| Component                                    | Current TRL | Target TRL | Evidence Required                                          | Source Docs                                                                       |
| -------------------------------------------- | ----------- | ---------- | ---------------------------------------------------------- | --------------------------------------------------------------------------------- |
| DIP Core (API, workflow, decision trace)     | 4-5         | 6-7        | pilot-grade reliability, traceability, governance logs     | docs/grant/15-dip-architecture.en.md, docs/grant/16-decision-engine.en.md         |
| ML Pipeline (training, registry, monitoring) | 3-5         | 5-6        | reproducible evaluation, drift controls, rollback evidence | docs/grant/18-model-registry.en.md, docs/grant/23-model-lifecycle.en.md           |
| Dzvin.co Integration Layer                   | 5-6         | 7          | stable operational integration + adoption metrics          | docs/grant/31-dzvin.en.md, docs/grant/33-integration.en.md                        |
| Explainability Stack                         | 4-5         | 6          | faithfulness + user trust validation                       | docs/grant/20-explainability.en.md, docs/grant/29-explainability-validation.en.md |

## Evidence Rules

- Each TRL jump must be supported by tests, metrics, and reproducibility artifacts.
- TRL status must be updated after each major milestone.

## Horizon Europe References

- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
