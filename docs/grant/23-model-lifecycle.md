# Model Lifecycle

Мова: Українська (default) | [English](23-model-lifecycle.en.md)

## Document Metadata
- Owner: MLOps Lead
- Contributors: ML Team, Platform Team, QA
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Описати повний lifecycle моделей від ідеї до deprecation у межах DIP + Dzvin.co.

## Lifecycle Stages
1. Problem framing
2. Data and feature freeze
3. Training and offline validation
4. Registry approval
5. Controlled deployment
6. Monitoring and online evaluation
7. Retraining or rollback
8. Deprecation and archive

## Entry and Exit Criteria
- Кожен етап має чіткі gates і required artifacts.
- Перехід між етапами можливий лише за наявності evidences.

## Monitoring in Production
- Predictive quality metrics.
- Calibration and drift metrics.
- Confidence distribution.
- Policy conflict rates.

## Retraining Triggers
- Sustained metric degradation.
- Data distribution shift.
- Label/ground-truth evolution.

## Rollback Triggers
- Critical safety alerts.
- Severe calibration drift.
- Elevated false-high-risk rate.

## Documentation Requirements
- Model card per version.
- Evaluation report per release.
- Bias and safety checklists.
- Deployment and rollback logs.

## Acceptance Criteria
- Для кожної deployed model існує end-to-end lifecycle trace.
- Retraining/rollback сценарії протестовані.
- Lifecycle інтегрований з policy governance.

## Links
- Related docs: 18-model-registry.md, 24-experiment-tracking.md, 25-evaluation.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
