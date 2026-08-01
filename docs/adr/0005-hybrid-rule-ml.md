# ADR-0005: Hybrid Rule+ML Decision Policy

## Status
Accepted

## Context
Rules-only недостатньо гнучкі, ML-only недостатньо прозорі для чутливого домену.

## Options
1. Rules-only
2. ML-only
3. Hybrid rule+ML with policy governance

## Decision
Вибрано hybrid rule+ML з trust-gated policy layer.

## Consequences
- Плюси: кращий баланс interpretability/quality/safety.
- Мінуси: вища складність оцінки та runtime governance.
