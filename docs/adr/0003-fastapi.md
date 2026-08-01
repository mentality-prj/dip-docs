# ADR-0003: FastAPI for DIP API Layer

## Status
Accepted

## Context
Потрібен API-first підхід зі швидкою розробкою typed contracts і async readiness.

## Options
1. FastAPI
2. Flask
3. Django REST

## Decision
Обрано FastAPI.

## Consequences
- Плюси: Pydantic validation, async support, clear OpenAPI generation.
- Мінуси: потреба дисципліни в backward compatibility для evolving contracts.
