# Statistical Analysis

## Document Metadata
- Owner: Biostatistics Lead
- Contributors: Data Scientists, Research Analysts
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Описати статистичний план для перевірки гіпотез, оцінки невизначеності та контролю помилок висновків.

## Analysis Principles
- Effect sizes first, p-values second.
- Confidence intervals for all primary effects.
- Predefined hypothesis families.
- Transparent handling of missing data.

## Primary Test Toolbox
- Mann-Whitney U for non-normal two-group comparisons.
- ANOVA / Welch ANOVA for multi-group comparisons.
- Chi-square tests for categorical distributions.
- Bootstrap intervals for unstable distributions.
- ROC/AUPRC analysis for ranking quality.

## Calibration and Reliability
- Brier score
- Expected calibration error
- Reliability curves by cohort

## Multiple Testing Control
- FDR control for exploratory blocks.
- Family-wise error control for confirmatory primary endpoints.

## Missing Data Policy
- Missingness diagnostics (MCAR/MAR plausibility checks).
- Multiple imputation where valid.
- Sensitivity analysis with complete-case comparison.

## Drift and Temporal Analysis
- Rolling-window metric deltas.
- Change-point monitoring.
- Confidence bounds for drift indicators.

## Practical Significance Thresholds
- Define minimal important difference per metric.
- Report both statistical and operational significance.

## Sample Size Logic
- Power targets for primary comparisons.
- Minimal conclusive sample per segment.
- Early stopping and futility criteria for online tests.

## Reproducible Analysis Stack
- Versioned scripts and manifests.
- Fixed random seeds for bootstrap and splits.
- Immutable run metadata references.

## Acceptance Criteria
- Для кожної RQ визначено статистичний тест і припущення.
- Є план корекції на множинні порівняння.
- Всі primary results мають CI + effect size.

## Links
- Related docs: 05-research-questions.md, 06-methodology.md, 25-evaluation.md, 30-reproducibility.md
