# ADR-0007: Multi-Tenancy Model

## Status

Accepted

## Context

DIP and Dzvin.co must isolate data and execution context across organizations and tenants.

## Options

1. Shared tenant-unaware model
2. Separate deployments per tenant
3. Tenant-scoped logical isolation on shared platform

## Decision

Tenant-scoped logical isolation on a shared platform is adopted.

## Consequences

- Access control and audit become mandatory at every decision boundary.
- Lower infrastructure duplication than full per-tenant deployments.
