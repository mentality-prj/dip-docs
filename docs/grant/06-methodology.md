# Research Methodology

## Document Metadata
- Owner: Research Methodology Lead
- Contributors: Scientific Coordinator, ML Lead, Product Research
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Описати методологію дослідження для перевірки гіпотез щодо hybrid decision intelligence, explainability, personalization і operational impact.

## Methodological Framework
- Quantitative longitudinal analysis.
- Controlled online evaluation (A/B and policy variants).
- Retrospective and prospective cohort comparisons.
- Mixed-method user validation for explainability.

## Research Phases
1. Baseline characterization and data audit.
2. Hypothesis-driven experiment design.
3. Offline model/rule evaluation.
4. Online policy evaluation in controlled rollout.
5. Replication and reproducibility checks.

## Unit of Analysis
- Individual-level trajectories (privacy-preserving context).
- Team-level aggregates.
- Company-level decision outcomes.

## Causal and Non-Causal Claims Policy
- Correlation and predictive utility claims allowed with clear caveats.
- Causal claims only where design supports it.
- Clinical claims out of scope at this stage.

## Validity Strategy
- Internal validity: strict temporal splits, leakage controls.
- External validity: segment-based robustness checks.
- Construct validity: alignment of labels with business/clinical meaning.

## Statistical Strategy (High Level)
- Effect size reporting alongside p-values.
- Confidence intervals for key metrics.
- Bootstrap where distributional assumptions are weak.
- Multiple-comparison controls where needed.

## Bias and Fairness Strategy
- Representation and performance parity checks.
- Monitoring disparate error rates.
- Mitigation through feature/policy adjustments.

## Ethics and Safety Integration
- Role-based explanation exposure.
- Human-in-the-loop for high-risk/low-confidence outcomes.
- Incident logging and escalation procedures.

## Reproducibility Requirements
- Versioned datasets/features/models/policies.
- Fixed random seeds where applicable.
- Experiment manifests and immutable run logs.

## Evidence Outputs
- Experiment reports.
- Policy performance dashboards.
- Bias and safety reports.
- Decision trace audits.

## Acceptance Criteria
- Кожне RQ має відповідний метод і метрику перевірки.
- Є чітке розділення exploratory vs confirmatory analyses.
- Методологія підтримує reviewer-level auditability.

## Links
- Related docs: 07-experimental-design.md, 12-statistics.md, 25-evaluation.md, 30-reproducibility.md
