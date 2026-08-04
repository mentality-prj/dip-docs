# ADR-0008: Event and Audit Model

## Status

Accepted

## Context

The project requires auditable decision traces, experiment evidence and operational risk control.

## Options

1. Minimal logs only
2. Separate analytics store without audit guarantees
3. Structured event and audit model with immutable traces

## Decision

Structured event and audit model with immutable traces is adopted.

## Consequences

- Decision and policy changes can be replayed and reviewed.
- Audit volume and storage costs increase, but evidence quality improves.
