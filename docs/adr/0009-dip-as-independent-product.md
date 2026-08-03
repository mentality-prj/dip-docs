# ADR-0009: DIP as Independent Product

## Status
Accepted

## Context
DIP must remain reusable across multiple products and domains, rather than becoming an internal module of Dzvin.co.

## Options
1. DIP embedded directly in Dzvin.co
2. DIP as internal library only
3. DIP as an independent platform product with public API boundaries

## Decision
DIP is maintained as an independent platform product.

## Consequences
- Clear separation between platform core and application layer.
- Easier reuse for future products and grant narratives.
