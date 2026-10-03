# NOSTRADAMUS OC1 — QDIP Agro Decision Runtime Concept Note

Status: application draft; use only after GO gate in `README.md`

## Working title

**QDIP Agro Decision Runtime: Integrated Water and Crop Decision Support on the NOSTRADAMUS Platform**

## Challenge

Farm decisions combine weather/climate signals, soil/water state, operational constraints and competing objectives. Data may exist in separate services while the actual decision — what action to take, under which constraints and uncertainty — remains application-specific.

## Proposed application

Build an open grant-specific application and agriculture adapter that converts NOSTRADAMUS data/services into a structured DecisionSpec, compiles it into the existing QDIP Canonical Decision IR and evaluates feasible actions under uncertainty.

Initial Topic 5 pairing to validate against technical documentation:

- T1 sustainable crop-production optimisation;
- T3 water-resource efficiency and drought resilience.

The exact decision action must be selected from what the NOSTRADAMUS platform can support with decision-time data and meaningful validation — for example bounded irrigation/timing/resource allocation rather than an unsupported broad 'farm optimiser'.

## Technical contribution

- explicit separation of data availability from executable decision semantics;
- constraint-valid action generation;
- uncertainty-aware utility/risk evaluation;
- audit/replay of why an action was feasible/recommended;
- reusable agriculture adapter over unchanged QDIP Core;
- measurable integration-effort and decision-quality evidence.

## Validation

Compare QDIP application decisions against a credible call/domain baseline under identical information and constraints. Report:

- feasibility/hard-constraint violations;
- domain decision metric defined before evaluation;
- outcome or validated proxy supported by the call data;
- human correction/decision workflow;
- integration/engineering effort;
- reproducibility and audit completeness.

Do not claim yield, water, cost or sustainability improvement before the actual evaluation supports it.

## Deliverables

1. open-source grant-specific application/adapter compatible with the approved IP boundary;
2. NOSTRADAMUS platform integration;
3. bounded farm decision benchmark and baseline;
4. validation/evidence report;
5. reproducible demo;
6. exploitation/reuse plan for QDIP and agriculture users.

## Main unresolved items

- exact platform APIs/datasets usable for T1+T3;
- applicant legal entity and TRL proof;
- official open-source licence/background-IP obligations;
- end-user/validation access;
- exact action/objective that can be evaluated credibly within 12 months.