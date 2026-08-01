# ADR-0004: Plugin SDK for Extensibility

## Status
Accepted

## Context
Потрібно масштабувати DIP без модифікації core при додаванні доменних або ML capabilities.

## Options
1. Plugin SDK with manifest and capability model
2. Direct in-core module additions
3. External sidecar-only integration

## Decision
Вибрано Plugin SDK підхід.

## Consequences
- Плюси: контрольована extensibility, швидше domain scaling.
- Мінуси: складніша governance модель (compatibility, security review, deprecation path).
