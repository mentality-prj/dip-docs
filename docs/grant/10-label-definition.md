# Label Definition

## Document Metadata
- Owner: ML Lead
- Contributors: Decision Science, Clinical Advisor, Data Team
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Визначити цільові labels для training/evaluation і формальні правила їх побудови.

## Label Catalog (Draft)
- High Risk
- Medium Risk
- Low Risk
- Burnout Risk Increase
- Improvement Signal
- Relapse Signal

## Label Design Principles
- Operationally meaningful.
- Time-bounded and reproducible.
- Interpretable for governance/audit.
- Compatible with multi-level granularity.

## Example Definitions (to calibrate)
- High Risk: riskScore >= threshold_high with confidence guard.
- Medium Risk: threshold_mid <= riskScore < threshold_high.
- Improvement: sustained positive trend across defined window.
- Relapse: deterioration after previous improvement period.

## Label Windows
- Short window: 7-14 days
- Medium window: 30 days
- Long window: 60-90 days

## Ambiguity Handling
- Inconclusive label when evidence is insufficient.
- Conflict flags when rules and ML strongly disagree.

## Threshold Governance
- Initial thresholds from baseline evidence.
- Segment-level calibration where justified.
- Change log for threshold revisions.

## Quality Checks
- Label stability across reruns.
- Class balance monitoring.
- Agreement with external anchors (where available).

## Acceptance Criteria
- Кожен label має формулу, вікно, і justification.
- Є policy для inconclusive cases.
- Версії label logic трасуються у model/experiment metadata.

## Links
- Related docs: 11-ground-truth.md, 12-statistics.md, 26-metrics.md
