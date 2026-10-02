# 03 — Research Hypothesis

## Research objective

Test whether heterogeneous structured operational decision problems can be represented through a shared formal decision semantics and executed through one domain-agnostic runtime while preserving decision quality relative to specialized implementations and materially reducing total engineering effort.

## Main research question

Can a frozen Canonical Decision IR and generic runtime transfer across heterogeneous operational domains without introducing new domain semantics into Core and without materially degrading decision quality?

## Primary empirical claim

For each validation domain `d ∈ {A, B, C}`:

```text
NR_QDIP^(d) <= NR_specialized^(d) + epsilon_d
```

and independently:

```text
E_QDIP^(d) <= 0.5 * E_specialized^(d)
```

The claim must hold per-domain. Success in one domain cannot compensate for failure in another.

## Reference-normalized regret/loss

For a utility-maximization problem:

```text
NR_d = (U_ref,d - U_d) / S_d
```

where:

- `U_ref,d` follows a pre-registered hierarchy: certified optimum → certified bound where mathematically usable → pre-registered best-known reference;
- `S_d > 0` is a domain-specific natural scale fixed before experiment execution and independent of results from QDIP and all compared systems;
- the metric must be adapted consistently for loss-minimization formulations.

If `U_ref,d` is not a certified optimum, the result must be described as reference-normalized regret/loss, not oracle regret.

## Engineering effort

Observed MVP engineering effort is:

```text
E_d =
  E_model
+ E_implementation
+ E_test
+ E_integration
+ E_deployment
+ E_audit
```

Projected maintenance is reported separately and is not included in the primary MVP engineering gate.

Effort comparison requires equal scope, equivalent quality target, equivalent testing/deployment/audit requirements and comparable contributor competence.

## Hypotheses

### H1 — Decision-quality preservation

QDIP is non-inferior to an equal-scope specialized implementation according to the pre-registered `NR_d` and `epsilon_d` for each domain.

### H2 — Engineering reduction

QDIP reduces observed total engineering effort by at least 50% relative to the equal-scope specialized implementation for each domain.

### H3 — Semantic transferability

State, actions/decision variables, constraints, uncertainty, objectives/utility, risk and outcome semantics can be represented by the frozen Canonical Decision IR across all reference domains.

### H4 — Core transferability

After the freeze point, Test C requires zero functional Core changes and zero semantic changes to Canonical Decision IR or the extension API.

### H5 — Economic verifiability

QDIP can record expected model-implied utility, observed realized utility, constraint outcomes, reference-normalized regret/loss and benchmark differences in a replayable and auditable form.

Observed realized utility is not automatically interpreted as causal uplift; causal claims require a credible counterfactual design.

## Generalization failure

Test C fails the Universal Runtime thesis if any of the following is required after freeze:

- a new constraint semantic;
- a new objective/utility semantic;
- a new transition/observation semantic required by the declared problem class;
- a new solver semantic rather than a solver adapter;
- a plugin that implements a complete bespoke decision pipeline;
- a functional Core change.

## Thesis falsification

The central thesis is falsified for the MVP if, in any mandatory domain:

- decision-quality non-inferiority fails; or
- engineering reduction is below 50%; or
- the frozen IR/API cannot express the problem without semantic extension.
