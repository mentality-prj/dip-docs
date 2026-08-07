# Traceability Matrix

Language: [Українська (default)](01-traceability-matrix.md) | English

## Purpose

Provide an end-to-end evidence chain:
Research Question -> Hypothesis -> Dataset -> Features -> Experiment -> Metrics -> Result -> Scientific Claim.

## Matrix

| RQ                         | Hypothesis                                 | Dataset Source                            | Feature Set                             | Experiment ID | Metrics                                | Result Artifact                               | Scientific Claim                                             | Grant Section                    |
| -------------------------- | ------------------------------------------ | ----------------------------------------- | --------------------------------------- | ------------- | -------------------------------------- | --------------------------------------------- | ------------------------------------------------------------ | -------------------------------- |
| RQ1 Personalization Effect | H1 Adaptive baseline > population baseline | docs/grant/08-dataset-specification.en.md | docs/grant/09-feature-engineering.en.md | EXP-AB-001    | Calibration error, Precision@high-risk | docs/grant/25-evaluation.en.md                | C1 Personalization improves quality in the high-risk segment | proposal/01-excellence.en.md     |
| RQ2 Hybrid vs Single       | H2 Hybrid Rule+ML > Rules-only / ML-only   | docs/grant/08-dataset-specification.en.md | docs/grant/17-feature-store.en.md       | EXP-HYB-002   | AUROC, False alert rate                | docs/grant/26-metrics.en.md                   | C2 Hybrid improves the accuracy/safety balance               | proposal/01-excellence.en.md     |
| RQ3 Explainability Impact  | H3 Explainability increases trust/adoption | docs/grant/28-user-validation.en.md       | docs/grant/20-explainability.en.md      | EXP-XAI-003   | Trust uplift, Comprehension            | docs/grant/29-explainability-validation.en.md | C3 Explanations improve decision uptake                      | proposal/02-impact.en.md         |
| RQ4 Governance Robustness  | H4 Trust-gated policy reduces degradation  | docs/grant/24-experiment-tracking.en.md   | docs/grant/16-decision-engine.en.md     | EXP-GOV-004   | Degradation duration, Rollback rate    | docs/grant/25-evaluation.en.md                | C4 Governance loops improve stability                        | proposal/03-implementation.en.md |
| RQ5 Transferability        | H5 DIP reuse reduces integration effort    | docs/grant/33-integration.en.md           | docs/grant/15-dip-architecture.en.md    | EXP-TRF-005   | Time-to-first-value, Reuse ratio       | docs/grant/38-impact.en.md                    | C5 The platform approach is transferable                     | proposal/02-impact.en.md         |

## Usage Rule

- No statement in `docs/proposal/*` should be published without a reference to a row in this matrix.
- Each matrix row must have an owner and date of latest validation.

## Horizon Europe References

- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
