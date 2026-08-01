# TRL Mapping and Evidence

## Мета
Показати перехід Current TRL -> Target TRL -> Evidence для ключових компонентів.

## Таблиця TRL
| Component | Current TRL | Target TRL | Evidence Required | Source Docs |
|-----------|-------------|------------|-------------------|-------------|
| DIP Core (API, workflow, decision trace) | 4-5 | 6-7 | pilot-grade reliability, traceability, governance logs | docs/grant/15-dip-architecture.md, docs/grant/16-decision-engine.md |
| ML Pipeline (training, registry, monitoring) | 3-5 | 5-6 | reproducible evaluation, drift controls, rollback evidence | docs/grant/18-model-registry.md, docs/grant/23-model-lifecycle.md |
| Dzvin.co Integration Layer | 5-6 | 7 | stable operational integration + adoption metrics | docs/grant/31-dzvin.md, docs/grant/33-integration.md |
| Explainability Stack | 4-5 | 6 | faithfulness + user trust validation | docs/grant/20-explainability.md, docs/grant/29-explainability-validation.md |

## Правила доказовості
- Кожен TRL jump підтверджується тестами, метриками та артефактами відтворюваності.
- TRL-оцінка оновлюється після кожного major milestone.
