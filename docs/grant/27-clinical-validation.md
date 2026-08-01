# Clinical Validation

## Document Metadata
- Owner: Clinical Research Coordinator
- Contributors: Ethics Lead, Product Research, External Advisors
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Визначити рамку клінічно орієнтованої валідації для decision support сценаріїв без позиціонування системи як медичного діагностичного виробу на цьому етапі.

## Validation Objective
Перевірити, що risk/recommendation outputs:
- узгоджуються з очікуваними психометричними патернами;
- не створюють небезпечних або хибно-категоричних інтерпретацій;
- підтримують своєчасну ескалацію за високого ризику.

## Scope
- In scope: clinical plausibility and safety alignment.
- Out of scope: formal diagnostic claims.

## Validation Components
- Concordance with standardized questionnaires (where available).
- Review of explanation language safety.
- Escalation policy review for high-risk signals.
- Monitoring adverse interpretation incidents.

## Human Oversight
- Clinical advisory panel for protocol review.
- Defined referral/escalation guidance.
- Periodic review of high-risk false positives/negatives.

## Safety Triggers
- Low confidence + high risk combination.
- Contradictory signals over short windows.
- Repeated worsening without response uptake.

## Outputs
- Clinical plausibility report.
- Safety incident log.
- Recommendations for policy threshold adjustment.

## Limitations
- Self-report dependency.
- Non-clinical context for many users.
- Heterogeneous baseline mental states.

## Acceptance Criteria
- Всі клінічно чутливі сценарії мають human oversight policy.
- В explanation-комунікації немає діагностичних тверджень.
- Є documented escalation pathway.

## Links
- Related docs: 20-explainability.md, 22-uncertainty.md, 36-gdpr.md, 37-ethics.md
