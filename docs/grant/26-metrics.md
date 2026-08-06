# Metrics

Мова: Українська (default) | [English](26-metrics.en.md)

## Document Metadata
- Owner: Metrics Lead
- Contributors: Data Science, Product Analytics, Research Lead
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Визначити метрики успіху для predictive quality, decision quality, adoption, safety and impact.

## Metric Layers
- Predictive metrics
- Decision metrics
- User/adoption metrics
- Safety/governance metrics
- Business/impact metrics

## Predictive Metrics
- AUROC
- AUPRC
- Calibration error
- Brier score

## Decision Metrics
- Precision@high-risk alerts
- False alert rate
- Disagreement resolution quality
- Time-to-action after signal

## Explainability and Trust Metrics
- Comprehension score
- Trust score uplift
- Explanation usefulness rating

## Governance Metrics
- Drift alert frequency
- Mitigation activation rate
- Rollback count
- Policy stability index

## Operational Metrics
- Inference latency
- Pipeline freshness SLA adherence
- Data quality pass rate

## Metric Governance
- Primary vs secondary metrics registry.
- Threshold ownership.
- Change control for metric definitions.

## Acceptance Criteria
- Для кожного RQ визначено primary metrics.
- Всі metrics мають formulas і thresholds.
- Є dashboard mapping metrics -> decision gates.

## Links
- Related docs: 25-evaluation.md, 12-statistics.md, 38-impact.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
