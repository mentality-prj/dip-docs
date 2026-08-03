# ADR-0006: Explainability-First Decision Contract

## Status
Accepted

## Context
Чутливий домен потребує пояснень як частини рішення, а не post-hoc UI add-on.

## Options
1. Explainability as optional UI layer
2. Explainability as diagnostic only
3. Explainability as part of core decision contract

## Decision
Пояснюваність є частиною core decision contract.

## Consequences
- Кожне high-impact рішення повинно повертати trace, rationale і confidence context.
- API contract стає багатшим, але більш придатним для аудиту і грантової валідації.
