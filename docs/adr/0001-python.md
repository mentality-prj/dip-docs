# ADR-0001: Python as DIP Core Language

## Status
Accepted

## Context
DIP потребує швидкого розвитку AI/ML integration, data pipelines і explainability tooling.

## Options
1. Python
2. TypeScript/Node.js
3. JVM stack

## Decision
Обрано Python для core DIP.

## Consequences
- Плюси: сильна AI/ML екосистема, швидкий R&D цикл.
- Мінуси: більше уваги до performance tuning у high-load API paths.
