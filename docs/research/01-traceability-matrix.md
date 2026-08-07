# Traceability Matrix

Мова: Українська (default) | [English](01-traceability-matrix.en.md)

## Мета

Забезпечити наскрізний ланцюг доказів:
Research Question -> Hypothesis -> Dataset -> Features -> Experiment -> Metrics -> Result -> Scientific Claim.

## Матриця

| RQ                         | Hypothesis                                 | Dataset Source                         | Feature Set                          | Experiment ID | Metrics                                | Result Artifact                            | Scientific Claim                                       | Grant Section                 |
| -------------------------- | ------------------------------------------ | -------------------------------------- | ------------------------------------ | ------------- | -------------------------------------- | ------------------------------------------ | ------------------------------------------------------ | ----------------------------- |
| RQ1 Personalization Effect | H1 Adaptive baseline > population baseline | docs/grant/08-dataset-specification.md | docs/grant/09-feature-engineering.md | EXP-AB-001    | Calibration error, Precision@high-risk | docs/grant/25-evaluation.md                | C1 Персоналізація підвищує якість у high-risk сегменті | proposal/01-excellence.md     |
| RQ2 Hybrid vs Single       | H2 Hybrid Rule+ML > Rules-only / ML-only   | docs/grant/08-dataset-specification.md | docs/grant/17-feature-store.md       | EXP-HYB-002   | AUROC, False alert rate                | docs/grant/26-metrics.md                   | C2 Hybrid покращує баланс accuracy/safety              | proposal/01-excellence.md     |
| RQ3 Explainability Impact  | H3 Explainability збільшує trust/adoption  | docs/grant/28-user-validation.md       | docs/grant/20-explainability.md      | EXP-XAI-003   | Trust uplift, Comprehension            | docs/grant/29-explainability-validation.md | C3 Пояснення покращують прийняття рішень               | proposal/02-impact.md         |
| RQ4 Governance Robustness  | H4 Trust-gated policy знижує деградацію    | docs/grant/24-experiment-tracking.md   | docs/grant/16-decision-engine.md     | EXP-GOV-004   | Degradation duration, Rollback rate    | docs/grant/25-evaluation.md                | C4 Governance loops підвищують стабільність            | proposal/03-implementation.md |
| RQ5 Transferability        | H5 DIP reuse скорочує integration effort   | docs/grant/33-integration.md           | docs/grant/15-dip-architecture.md    | EXP-TRF-005   | Time-to-first-value, Reuse ratio       | docs/grant/38-impact.md                    | C5 Платформний підхід переносимий                      | proposal/02-impact.md         |

## Правило використання

- Жодне твердження в `docs/proposal/*` не публікується без посилання на рядок цієї матриці.
- Кожен рядок матриці повинен мати owner та дату останньої валідації.

## Horizon Europe References

- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
