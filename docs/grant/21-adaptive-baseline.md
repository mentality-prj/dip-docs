# Adaptive Baseline

## Document Metadata
- Owner: Decision Science Lead
- Contributors: ML Team, Analytics Team
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Описати механізм adaptive baseline для персоналізованих і командних risk оцінок.

## Motivation
Static thresholds погано працюють у різних популяціях і часових фазах.
Adaptive baseline дозволяє оцінювати відхилення від індивідуальної/командної норми.

## Baseline Levels
- Individual baseline
- Team baseline
- Company baseline

## Baseline Components
- Recent central tendency
- Volatility profile
- Trend factor
- Engagement-adjusted confidence

## Update Policy
- Rolling windows with minimal sample requirements.
- Smoothing for noisy trajectories.
- Freeze logic during data outages or instability.

## Use in Decision Engine
- Baseline feeds anomaly and deviation terms.
- Baseline quality impacts confidence and policy routing.
- Severe baseline shifts trigger diagnostics flags.

## Guardrails
- Minimum evidence threshold.
- Drift-aware recalibration triggers.
- Conservative fallback when baseline confidence is low.

## Evaluation Criteria
- Better calibration in heterogeneous cohorts.
- Reduced false alerts vs static baseline.
- Stability under missingness and engagement variance.

## Acceptance Criteria
- Baseline logic versioned and reproducible.
- Quality/confidence of baseline exposed to policy layer.
- Documented fallback path when baseline unreliable.

## Links
- Related docs: 16-decision-engine.md, 22-uncertainty.md, 26-metrics.md
