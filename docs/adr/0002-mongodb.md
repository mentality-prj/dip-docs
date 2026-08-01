# ADR-0002: MongoDB for Flexible Domain and Event Data

## Status
Accepted

## Context
Потрібні гнучкі схеми для workflow, decision artifacts, audit/event records.

## Options
1. MongoDB
2. Relational-only approach
3. Hybrid polyglot storage from day one

## Decision
MongoDB використовується як primary operational store для поточного етапу.

## Consequences
- Плюси: schema flexibility, швидка ітерація доменної моделі.
- Мінуси: необхідні жорсткі governance правила для consistency і indexing.
