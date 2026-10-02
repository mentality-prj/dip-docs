# 02 — State of the Art

Status: initial grant-facing synthesis; expand with peer-reviewed literature matrix before submission.

## 1. Scope

QDIP should not claim novelty from optimization itself. Mature solver, algebraic-modeling, constraint-modeling and enterprise-planning ecosystems already exist. The research gap being tested is whether a reusable formal decision representation and runtime can reduce the engineering required to build heterogeneous operational decision systems while preserving decision quality.

The novelty claim must therefore be evaluated against both enterprise systems and lightweight optimization/modeling frameworks.

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

SAP Integrated Business Planning provides constrained planning, heuristics and optimization algorithms for operational planning domains.

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

### 2.3 Algebraic and constraint modeling frameworks

The relevant comparison set is broader than Pyomo and OR-Tools. It includes modeling systems such as:

- Pyomo;
- JuMP;
- AMPL;
- MiniZinc;
- OR-Tools / CP-SAT;
- solver-native modeling APIs.

These systems already provide strong abstractions over mathematical optimization and can significantly reduce bespoke solver code.

Representative references:

- https://www.pyomo.org/
- https://jump.dev/
- https://ampl.com/
- https://www.minizinc.org/
- https://developers.google.com/optimization

Strengths:

- mature mathematical modeling abstractions;
- symbolic constraints/objectives;
- broad solver access;
- strong algorithmic foundations;
- relatively low implementation and/or license cost compared with heavyweight enterprise suites.

Critical boundary relative to QDIP thesis:

QDIP cannot claim novelty merely because it defines a Canonical Decision IR. Existing modeling languages already separate model semantics from solver implementation.

The QDIP claim must instead be tested at the larger decision-system lifecycle boundary:

```text
formal decision contract
+ canonical optimization semantics
+ uncertainty/risk semantics
+ solver abstraction
+ replay/backtesting
+ realized-outcome ingestion
+ reference-normalized evaluation
+ audit/reproducibility
+ cross-domain transfer with measured engineering reduction
```

Whether this combination produces a material engineering advantage is an empirical question, not an assumed differentiator.

### 2.4 Decision automation / workflow / enterprise AI platforms

Before submission, the literature/product matrix must also cover systems that connect data, models, operational workflows and decisions. This includes enterprise decision automation, planning, AI orchestration and operational-intelligence platforms.

The comparison must distinguish:

- analytics;
- prediction;
- mathematical optimization;
- workflow automation;
- decision execution;
- audit/replay;
- reusable decision semantics.

## 3. Research gap

The target gap is not "missing optimization algorithms" or "missing modeling languages". The target gap is the repeated engineering required to move from a business/operational decision problem to a production-grade, auditable decision system.

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

QDIP tests whether enough of this lifecycle can be captured by a frozen reusable abstraction layer to cut domain engineering effort materially without degrading decision quality.

## 4. Novelty claim boundary

Do not claim:

- a new universal optimizer;
- a novel algebraic modeling language merely because Canonical Decision IR exists;
- mathematical superiority to enterprise/specialized optimizers solving the same formal problem;
- automatic causal economic uplift;
- universal applicability to arbitrary decisions.

The defensible claim under test is:

> A domain-agnostic formal decision representation plus reusable execution, uncertainty/risk, evaluation, replay and audit runtime can transfer across heterogeneous structured operational decision problems while preserving non-inferior decision quality and materially reducing domain engineering effort.

## 5. Evidence required before grant submission

The state-of-the-art claim must be supported by:

- peer-reviewed literature on algebraic/optimization modeling languages;
- decision modeling / decision intelligence literature;
- stochastic and robust optimization literature;
- reusable solver/IR frameworks;
- enterprise planning products;
- workflow/decision automation systems;
- evidence that the proposed lifecycle-level combination is not already available with the same transferability/effort properties.

Create or update the literature matrix before submission and distinguish clearly between academic novelty, engineering novelty and product differentiation.
