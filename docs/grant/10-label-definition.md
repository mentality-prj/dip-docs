# Label Definition

Мова: Українська (default) | [English](10-label-definition.en.md)

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

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
