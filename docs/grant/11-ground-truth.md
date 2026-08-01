# Ground Truth

## Document Metadata
- Owner: Research Quality Lead
- Contributors: Clinical Advisor, Data Science, Product Research
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Описати процес формування ground truth для оцінювання моделей і decision policies.

## Ground Truth Sources
- Longitudinal self-report trajectories.
- Psychometric checkpoints.
- Behavioral and engagement outcomes.
- Structured feedback signals on predicted events.

## Ground Truth Strategy
- Multi-source triangulation замість single-source truth.
- Time-aligned outcome windows.
- Confidence tagging for each truth instance.

## Annotation and Review
- Rule-based auto-labeling baseline.
- Human review for edge/high-impact cases.
- Disagreement adjudication workflow.

## Confidence Tiers
- High confidence: multiple converging sources.
- Medium confidence: limited but consistent evidence.
- Low confidence: sparse/conflicting signals.

## Noise and Uncertainty Handling
- Explicit inconclusive class.
- Weighted evaluation by confidence tier.
- Sensitivity analysis excluding low-confidence truths.

## Drift Control
- Periodic re-evaluation of truth construction rules.
- Monitoring shift in source reliability.

## Acceptance Criteria
- Ground truth protocol задокументований і відтворюваний.
- Є audit trail для manual adjudication.
- Усі evaluation reports містять confidence-stratified results.

## Links
- Related docs: 10-label-definition.md, 12-statistics.md, 25-evaluation.md, 30-reproducibility.md
