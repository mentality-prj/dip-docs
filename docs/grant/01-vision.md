# Vision

## Document Metadata
- Owner: Dzvin R&D Core Team
- Contributors: DIP Team, Dzvin.co Team, Clinical Advisors (to be assigned)
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft for internal alignment

## Purpose
Сформувати спільне бачення єдиного R&D-проєкту Dzvin.co + DIP, де DIP є універсальною Decision Intelligence Platform, а Dzvin.co є першим production use-case для mental wellbeing домену.

## Strategic Statement
Проєкт будується як дві взаємопов'язані системи з різними ролями:
- DIP: незалежна технологічна платформа для прийняття рішень, прогнозування, explainability, research lifecycle.
- Dzvin.co: доменний продукт для працівників, менеджерів та компаній, який використовує DIP через API-контракт.

Ключова стратегія: відокремити ядро інтелектуальних рішень від прикладного UX/бізнес-логіки, щоб:
- повторно використовувати R&D-результати у кількох продуктах;
- прискорити валідацію гіпотез без переписування платформенного ядра;
- забезпечити traceability від експерименту до production-рішення.

## Why Now
Поточний стан ринку створює три синхронні запити:
- компанії потребують пояснюваних сигналів ризику та actionable рекомендацій, а не тільки сирої аналітики;
- AI-рішення в wellbeing часто непрозорі та погано відтворювані;
- регуляторні й етичні вимоги (GDPR, AI governance) вимагають auditable pipelines.

## Mission
Створити відтворювану, пояснювану та доменно-агностичну платформу Decision Intelligence, яка може підтримувати mental health use-cases і масштабуватися в інші галузі без зміни core.

## Long-Term Vision (5+ years)
- DIP стає окремим reusable платформним продуктом з plugin-моделлю.
- Dzvin.co виступає еталонним доказом практичної цінності платформи у чутливому домені mental wellbeing.
- Кожен новий use-case додається через adapter + configuration + optional plugins.

## Design Principles
- Domain Independent ядро
- API First інтеграція
- Explainable by design
- Hybrid intelligence (rules + statistical + ML)
- Human-in-the-loop у high-impact сценаріях
- Privacy-first and auditable operations
- Reproducible research-to-production flow

## Product Boundary Model

### DIP (platform responsibilities)
- Rule/workflow evaluation
- Prediction execution and confidence outputs
- Decision trace and explanation artifacts
- Experiment and model lifecycle hooks
- Multi-tenant integration contract

### Dzvin.co (application responsibilities)
- End-user experiences (B2C wellbeing journeys)
- B2B analytics and management reporting
- Questionnaire and engagement flows
- Operational adoption and intervention delivery

## Value Proposition

### Scientific Value
- Можливість перевіряти гіпотези щодо персоналізації, explainability та hybrid decision logic у production-like середовищі.

### Product Value
- Швидший цикл впровадження нових моделей/правил без перебудови всього застосунку.

### Societal Value
- Підвищення якості рішень у сфері психічного здоров'я завдяки прозорим risk signals та validated intervention pathways.

## Non-Goals
- Не створювати моноліт, де продуктова логіка й AI-ядро злиті в один шар.
- Не обмежувати DIP тільки healthcare-доменом.
- Не позиціонувати ранні евристики як остаточно валідовані клінічні моделі.

## Success Criteria for Vision Alignment
- Єдина термінологія platform vs product затверджена командами.
- Кожен модуль Dzvin.co мапується на platform capability або application-only layer.
- Кожна R&D гіпотеза має шлях до експерименту та production signal.

## Open Strategic Risks
- Ризик надмірної складності через ранню генералізацію DIP.
- Ризик розриву між науковими метриками та операційними KPI замовників.
- Ризик переоцінки explainability ефекту без достатньої user validation.

## Decisions Enabled by This Document
- Чи подається Dzvin.co + DIP як єдиний R&D проєкт: так.
- Який об'єкт інновації у заявці: платформне decision ядро + validated domain application.
- Як масштабувати після гранту: через adapter-based reuse DIP.

## Links
- Related docs: 02-problem-statement.md, 04-scientific-novelty.md, 15-dip-architecture.md, 16-decision-engine.md
- Related references: EIC Pathfinder evaluation logic (Excellence, Impact, Implementation)
