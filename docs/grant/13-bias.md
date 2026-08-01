# Bias Analysis

## Document Metadata
- Owner: Responsible AI Lead
- Contributors: Data Science, Ethics Lead, Product Analytics
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Визначити підхід до виявлення, оцінки і зменшення bias у decision pipelines.

## Bias Risk Categories
- Sampling bias
- Participation bias
- Measurement bias (self-report artifacts)
- Label bias
- Policy bias from threshold settings

## Analysis Dimensions
- Across teams/company sizes.
- Across engagement levels.
- Across data completeness tiers.
- Across temporal periods.

## Core Fairness Checks
- Error rate comparison by segment.
- Calibration parity checks.
- Alert burden distribution.
- Disagreement distribution (rules vs ML).

## Mitigation Toolkit
- Reweighting and resampling.
- Segment-aware threshold calibration.
- Feature revision/removal for problematic proxies.
- Policy guardrails for vulnerable segments.

## Monitoring Cadence
- Pre-release bias audit.
- Rolling production bias dashboards.
- Trigger-based deep-dive review.

## Governance
- Bias findings logged with severity and owner.
- Mandatory mitigation plan for medium/high risk findings.
- Ethics board escalation for unresolved critical bias.

## Acceptance Criteria
- Bias analysis інтегровано у release gates.
- Є evidence that mitigations reduce detected disparities.
- Bias status включено в регулярний evaluation report.

## Links
- Related docs: 12-statistics.md, 14-data-quality.md, 37-ethics.md, 44-risk-management.md
