# Metrics

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
