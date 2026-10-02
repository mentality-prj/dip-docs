# 02 — State of the Art

Status: initial grant-facing synthesis; expand with peer-reviewed literature matrix before submission.

## 1. Scope

QDIP should not claim novelty from optimization itself. Mature solver and enterprise-planning ecosystems already exist. The research gap being tested is whether a reusable formal decision representation and runtime can reduce the engineering required to build heterogeneous operational decision systems while preserving decision quality.

## 2. Existing solution classes

### 2.1 BI and scenario-planning systems

Microsoft Power BI / Fabric provide mature analytics, governance, reporting and scenario-planning workflows. Fabric scenario planning allows users to create alternative plan versions, simulate assumptions, compare outcomes and preserve a governed base plan.

Relevant official references:

- https://learn.microsoft.com/en-us/power-bi/power-bi-overview
- https://learn.microsoft.com/en-us/fabric/iq/plan/planning-concept-scenario-planning

Strengths:

- enterprise analytics and semantic modeling;
- visualization and collaboration;
- governed scenario analysis;
- broad integration ecosystem.

Boundary relative to QDIP thesis:

- scenario analysis is not equivalent to a generic constrained decision runtime;
- the QDIP benchmark must compare decision outcomes, not dashboard functionality.

### 2.2 Enterprise operational optimization

SAP Integrated Business Planning provides constrained planning, finite heuristics and optimization algorithms for supply-planning domains. It can model supply networks, selected constraints, planning horizons and optimizer configurations.

Relevant official references:

- https://www.sap.com/products/scm/integrated-business-planning/features/response-and-supply-planning.html
- https://help.sap.com/docs/SAP_INTEGRATED_BUSINESS_PLANNING/

Strengths:

- mature domain semantics;
- operational planning integration;
- constrained optimization;
- enterprise governance and workflows.

Boundary relative to QDIP thesis:

- QDIP does not claim mathematically superior optimality to a specialized enterprise optimizer solving the same formal problem;
- the proposed advantage is comparable decision quality with materially lower domain-specific engineering and deployment effort.

### 2.3 Optimization modeling frameworks

Pyomo is an open-source Python optimization modeling language that separates model definition from underlying solvers. OR-Tools provides mature open-source combinatorial optimization capabilities, including routing, linear/integer programming and constraint programming.

Relevant official references:

- https://www.pyomo.org/
- https://developers.google.com/optimization

Strengths:

- mature optimization abstractions;
- broad solver access;
- strong algorithmic foundations;
- low license cost for the framework itself.

Boundary relative to QDIP thesis:

- solver/modeling frameworks do not by themselves provide a domain-independent decision contract, standardized uncertainty/risk semantics, realized-outcome ingestion, benchmark protocol, replay, economic verification and end-to-end decision audit;
- this boundary must be demonstrated empirically rather than asserted.

## 3. Research gap

The target gap is not "missing optimization algorithms". The target gap is the repeated engineering required to move from a business/operational decision problem to a production-grade decision system.

Typical bespoke work includes:

1. formalizing state and available actions;
2. defining domain constraints;
3. defining uncertainty and risk treatment;
4. defining business/economic utility;
5. mapping the model to solver-specific constructs;
6. integrating data sources;
7. building replay/backtesting;
8. recording decisions and realized outcomes;
9. implementing auditability and reproducibility;
10. deploying and maintaining the resulting pipeline.

QDIP tests whether enough of this lifecycle can be captured by a frozen reusable abstraction layer to cut total engineering effort by at least 50% without materially degrading decision quality.

## 4. Novelty claim boundary

Do not claim:

- a new universal optimizer;
- mathematical superiority to all enterprise optimizers;
- automatic causal economic uplift;
- universal applicability to arbitrary decisions.

The defensible claim under test is:

> A domain-agnostic formal decision representation plus reusable execution/evaluation runtime can transfer across heterogeneous structured operational decision problems while preserving non-inferior decision quality and materially reducing engineering effort.

## 5. Evidence required before grant submission

The state-of-the-art claim must be supported by:

- peer-reviewed literature on algebraic/optimization modeling languages;
- decision modeling / decision intelligence literature;
- stochastic and robust optimization literature;
- reusable solver/IR frameworks;
- enterprise planning products;
- workflow/decision automation systems;
- evidence that the proposed combination is not already available with the same transferability/effort properties.

Create or update the literature matrix before submission and distinguish clearly between academic novelty, engineering novelty and product differentiation.
