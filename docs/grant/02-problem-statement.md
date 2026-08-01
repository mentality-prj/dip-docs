# Problem Statement

## Document Metadata
- Owner: Research Lead
- Contributors: Product, Data Science, Clinical and Security stakeholders
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft for research framing

## Purpose
Формалізувати проблему, яку вирішує спільний проєкт Dzvin.co + DIP, у чотирьох вимірах: mental health, enterprise analytics, explainable AI, personalization.

## Problem 1: Mental Wellbeing Signal Fragmentation
Організації та користувачі мають багато окремих індикаторів (mood, stress, energy, focus, psychometric snapshots), але не мають інтегрованого decision layer, який:
- зводить сигнали до послідовного ризик-профілю;
- пояснює, чому саме такий висновок;
- прив'язує висновок до конкретних дій.

Наслідок: управлінські та індивідуальні рішення часто реактивні, а не превентивні.

## Problem 2: Enterprise Analytics Without Actionability
У B2B-сценаріях аналітика часто завершується дашбордом, а не керованою дією.
Типовий розрив:
- є метрика підвищеного стресу;
- немає формалізованого decision policy, яка перетворює це на пріоритетну рекомендацію;
- немає вбудованого контролю якості рішень у часі.

Наслідок: низький вплив аналітики на операційні зміни.

## Problem 3: Explainability and Trust Gap in AI Decisions
AI-рекомендації в чутливих доменах не приймаються без пояснення, confidence і auditability.
Критичні прогалини в типових системах:
- відсутність rule trace або feature-level rationale;
- неможливість перевірити відтворюваність рішення;
- слабка governance-модель для fallback, overrides і policy control.

Наслідок: обмежена довіра, складність аудиту та підвищений комплаєнс-ризик.

## Problem 4: Personalization vs Robustness Trade-off
Персоналізація покращує релевантність, але підвищує складність валідації:
- baseline користувача та команди динамічні;
- моделі можуть дрейфувати;
- fixed-threshold rule sets деградують на різних популяціях.

Наслідок: без adaptive design система або надто загальна, або нестабільна.

## Root Causes
- Змішування platform intelligence і application logic в одному кодовому шарі.
- Недостатня стандартизація decision artifacts (feature set, trace, confidence, policy signal).
- Відсутність єдиного research-to-production контуру.

## Current Baseline (Verified in Existing Stack)
- Є production-oriented бекенд Dzvin.co з B2C/B2B/R&D потоками.
- Є Decision Support модуль з deterministic rules, burnout index, impact estimation, change tracking.
- Є online evaluation, policy control, trust thresholds, diagnostics surfaces.
- Є окремий DIP репозиторій з API, workflow/rule execution та decision audit traces.

Це створює стартову інфраструктуру, але не закриває повністю наукові питання персоналізації, causal effect інтервенцій та зовнішньої валідності.

## Target Problem Resolution
Потрібна architecture-level відповідь:
- DIP як platform core для уніфікації rules/ML/explainability;
- Dzvin.co як validated first domain implementation;
- єдиний R&D протокол для експериментів, статистики, етики та відтворюваності.

## Evidence Gaps to Close in R&D Phase
- Наскільки hybrid rule+ML стабільніший за single-paradigm підходи.
- Який вплив explainability на adoption та quality of decisions.
- Які режими персоналізації дають приріст без втрати robustness.
- Яка межа переносимості підходу між доменами.

## Scope Boundaries
- In scope: decision intelligence для wellbeing і enterprise risk analytics.
- Out of scope: клінічний діагноз як медичний виріб у цьому етапі.
- Out of scope: повністю автономні high-impact рішення без human review.

## Success Criteria
- Проблема описана у вимірюваних термінах (inputs, decisions, outcomes).
- Кожна підпроблема має відповідний RQ та validation protocol.
- Визначено, які claims є operational, а які наукові.

## Links
- Related docs: 01-vision.md, 05-research-questions.md, 06-methodology.md, 25-evaluation.md
