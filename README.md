# DIP Docs Repository

Цей репозиторій містить повний комплект документації для R&D проєкту Dzvin.co + DIP і підготовки грантових заявок (від гіпотез і вимог до верифікації та proposal-пакета).

## Зміст

1. [Призначення репозиторію](#призначення-репозиторію)
2. [Швидка навігація](#швидка-навігація)
3. [Карта документації](#карта-документації)
4. [Рекомендований порядок роботи](#рекомендований-порядок-роботи)
5. [Операційні правила оновлення](#операційні-правила-оновлення)

## Призначення репозиторію

Репозиторій організований як керований ланцюг:

Research -> Requirements -> Architecture -> Implementation -> Verification -> Evidence -> Proposal

Це дозволяє:
- зберігати простежуваність від наукових тверджень до доказів;
- контролювати зміни через ADR і change log;
- збирати заявку з готових модулів, а не писати з нуля.

## Швидка навігація

- [Шар Grant Documentation](docs/grant/README.md)
- [Шар Research](docs/research/README.md)
- [Шар Proposal](docs/proposal/README.md)
- [System Requirements Specification](docs/specification/system-requirements.md)
- [Architecture Decision Records](docs/adr/README.md)
- [Verification Layer](docs/verification/README.md)
- [Risk Register](docs/operations/risk-register.md)
- [Deliverables Register](docs/operations/deliverables-register.md)
- [Change Log](docs/operations/change-log.md)

## Карта документації

### 1) Grant Base

Базовий корпус R&D і грантової документації:
- [Огляд і правила](docs/grant/README.md)
- [Додатки](docs/grant/appendices/A01-literature-matrix.md)
- [Data Dictionary](docs/grant/appendices/A02-dataset-dictionary.md)
- [Metrics Sheet](docs/grant/appendices/A03-metrics-calculation-sheet.md)

### 2) Research Layer

Зв'язок між гіпотезами, експериментами і доказами:
- [Traceability Matrix](docs/research/01-traceability-matrix.md)
- [Scientific Hypotheses](docs/research/02-scientific-hypotheses.md)
- [WP Success Criteria](docs/research/03-wp-success-criteria.md)
- [TRL Mapping and Evidence](docs/research/04-trl-mapping-evidence.md)
- [Technology Readiness Assessment](docs/research/05-technology-readiness-assessment.md)
- [Competitive Landscape](docs/research/06-competitive-landscape.md)
- [IP Strategy](docs/research/07-ip-strategy.md)
- [Consortium Handbook](docs/research/08-consortium-handbook.md)
- [Data Management Plan](docs/research/09-data-management-plan-dmp.md)
- [Experiment Registry](docs/research/experiment-registry.md)

### 3) Specification Layer

Функціональні та нефункціональні вимоги:
- [System Requirements Specification](docs/specification/system-requirements.md)

### 4) Architecture Governance

Ключові технічні рішення:
- [ADR Index](docs/adr/README.md)
- [ADR-0001 Python](docs/adr/0001-python.md)
- [ADR-0002 MongoDB](docs/adr/0002-mongodb.md)
- [ADR-0003 FastAPI](docs/adr/0003-fastapi.md)
- [ADR-0004 Plugin SDK](docs/adr/0004-plugin-sdk.md)
- [ADR-0005 Hybrid Rule+ML](docs/adr/0005-hybrid-rule-ml.md)
- [ADR-0006 Explainability First](docs/adr/0006-explainability-first.md)
- [ADR-0007 Multi-Tenancy Model](docs/adr/0007-multi-tenancy-model.md)
- [ADR-0008 Event and Audit Model](docs/adr/0008-event-audit-model.md)
- [ADR-0009 DIP as Independent Product](docs/adr/0009-dip-as-independent-product.md)

### 5) Operations and Control

Контроль виконання і змін:
- [Risk Register](docs/operations/risk-register.md)
- [Deliverables Register](docs/operations/deliverables-register.md)
- [Change Log](docs/operations/change-log.md)

### 6) Verification and Evidence

Верифікація вимог і доказова база:
- [Verification Plan](docs/verification/verification-plan.md)
- [Verification Matrix](docs/verification/verification-matrix.md)

### 7) Proposal Layer

Матеріали, які напряму збираються у заявку:
- [Proposal Overview](docs/proposal/README.md)
- [01 Excellence](docs/proposal/01-excellence.md)
- [02 Impact](docs/proposal/02-impact.md)
- [03 Implementation](docs/proposal/03-implementation.md)
- [04 Budget](docs/proposal/04-budget.md)
- [05 Consortium](docs/proposal/05-consortium.md)
- [06 Ethics](docs/proposal/06-ethics.md)

## Рекомендований порядок роботи

1. Оновити [Research Layer](docs/research/README.md): гіпотези, експерименти, критерії успіху.
2. Оновити [SRS](docs/specification/system-requirements.md) і перевірити відповідність FR/NFR.
3. За потреби додати новий ADR у [ADR Index](docs/adr/README.md).
4. Оновити [Deliverables Register](docs/operations/deliverables-register.md) і [Risk Register](docs/operations/risk-register.md).
5. Зафіксувати результати у [Verification Matrix](docs/verification/verification-matrix.md).
6. Після цього оновлювати розділи [Proposal](docs/proposal/README.md).

## Операційні правила оновлення

- Кожна суттєва зміна архітектури має бути відображена в ADR.
- Кожна вимога SRS повинна мати verification-статус.
- Кожен експеримент повинен бути зареєстрований в experiment registry.
- Кожен ризик повинен мати owner, trigger і contingency plan.
- Дані для грантових тверджень повинні посилатися на evidence-артефакти.
