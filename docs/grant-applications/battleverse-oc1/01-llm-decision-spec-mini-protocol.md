# BattleVerse OC1 — LLM → DecisionSpec Research Mini-Protocol

Status: draft pre-registration for GO/NO-GO proof
Scope: application-specific research experiment over the canonical QDIP runtime

## 1. Purpose

Determine whether an LLM-based semantic-intake layer is a genuine research contribution to QDIP rather than a cosmetic parser or chat wrapper.

The experiment tests whether ambiguous, partially structured mission/scenario text can be transformed into a formally validated `DecisionSpec` with controlled failure behavior and without materially degrading downstream QDIP decision quality relative to a manually structured reference.

The LLM is not the decision authority. QDIP remains authoritative for formal constraints, utility/risk semantics, feasibility, optimization and audit.

```text
Unstructured scenario / operator intent
                ↓
        LLM semantic extraction
                ↓
 ambiguity detection / abstention / questions
                ↓
      candidate DecisionSpec
                ↓
 deterministic schema + semantic validation
                ↓
       Canonical Decision IR
                ↓
          QDIP Runtime
                ↓
 decision / Pareto set / audit trace
```

## 2. Research contribution boundary

The work qualifies as research only if it addresses at least these non-trivial problems:

1. **Ambiguity handling** — distinguish extractable facts from unresolved or conflicting intent.
2. **Constraint extraction** — map natural-language constraints into typed formal constraints without silently changing their meaning.
3. **Objective/priority extraction** — distinguish hard requirements, preferences and optimization objectives.
4. **Controlled abstention / clarification** — reject or request clarification when the source text is insufficient for safe formalization.
5. **Semantic validation** — detect contradictions, unsupported constructs, missing mandatory fields and invalid units/domains.
6. **Failure-mode analysis** — characterize omission, hallucination, conflict-resolution and over-specification failures.
7. **Downstream impact** — measure how extraction errors affect feasibility and decision quality after QDIP execution.

A system that merely converts text to JSON without these mechanisms is a parser and does not satisfy the BattleVerse research-fit gate.

## 3. Experimental systems

### S0 — Manual Gold Structuring

A domain-qualified human converts each scenario into a canonical `DecisionSpec` using the same schema and semantics available to the LLM system.

This is the primary semantic reference.

### S1 — Naive LLM Extraction Ablation

LLM converts scenario text directly to `DecisionSpec`/JSON with schema formatting only.

No explicit ambiguity model, abstention policy or semantic validation beyond structural schema checks.

Purpose: demonstrate whether the research mechanisms add value beyond generic structured output.

### S2 — Proposed LLM Semantic Intake

LLM extraction plus:

- explicit evidence spans/provenance per extracted field;
- ambiguity/conflict labels;
- confidence or support classification;
- clarification/abstention policy;
- deterministic schema validation;
- QDIP semantic validation;
- constraint/objective consistency checks;
- failure logging and audit trace.

Only S2 is the proposed BattleVerse contribution.

## 4. Dataset / scenario set

Use a bounded set of mission-planning scenarios that exercise structured decision semantics without requiring classified information.

The dataset must contain at least these case classes:

- fully specified intent;
- omitted constraint;
- ambiguous deadline/resource statement;
- conflicting constraints;
- soft preference expressed as if it were mandatory;
- implicit objective;
- unsupported request outside current IR semantics;
- inconsistent units/quantities;
- multiple plausible interpretations;
- adversarial/noisy wording.

Before primary evaluation, freeze:

```text
scenario_set_version
scenario_count
train/dev/test split
scenario authorship process
gold-annotation process
adjudication rule
LLM model/version
prompt/template version
DecisionSpec schema/version
Canonical IR semantic version
validator version
QDIP runtime commit
random seeds / temperature / decoding config
```

Primary test scenarios must be held out from prompt/policy tuning.

## 5. Gold annotation

For each scenario, the gold package contains:

- canonical manual `DecisionSpec`;
- accepted alternative interpretations where genuinely ambiguous;
- hard constraints;
- soft constraints/preferences;
- objective terms;
- uncertainty inputs;
- required clarification points;
- unsupported/missing information markers;
- expected abstention/clarification behavior;
- provenance links to source text spans.

Where two qualified annotators disagree, use documented adjudication rather than silently selecting one interpretation.

## 6. Primary semantic metrics

### M1 — Field-level extraction correctness

Measure precision / recall / F1 over typed DecisionSpec facts.

Report separately for:

- state facts;
- actions/candidates;
- hard constraints;
- soft constraints;
- objectives;
- uncertainty parameters;
- temporal/horizon fields.

Do not collapse all field classes into one score only.

### M2 — Critical constraint preservation

For gold hard constraints, measure:

```text
ConstraintRecall = correctly_preserved_gold_constraints / all_gold_constraints
```

Also report false hard constraints introduced by the model.

Critical omissions and hallucinated hard constraints must be counted separately because they have asymmetric operational risk.

### M3 — Ambiguity / clarification performance

For scenarios requiring clarification or abstention, measure:

- ambiguity detection recall;
- false ambiguity rate;
- abstention precision/recall;
- clarification-question relevance;
- silent-assumption rate.

The key failure is not uncertainty itself; it is **unreported uncertainty that becomes formal semantics**.

### M4 — Semantic validity rate

```text
SemanticValidityRate =
  specs_passing_schema_and_semantic_validation /
  all_generated_specs
```

Additionally classify rejected specs by failure category.

### M5 — Provenance correctness

For extracted claims/constraints requiring source support, measure whether cited text spans actually support the formalized field.

This is used to detect unsupported hallucinated semantics.

## 7. Downstream QDIP metrics

### M6 — Infeasible-plan rate

Execute validated specs through the same QDIP runtime and frozen solver configuration.

Measure:

```text
InfeasiblePlanRate =
  scenarios_where_extracted_spec_causes_infeasibility_not_present_in_gold /
  evaluated_scenarios
```

Distinguish:

- legitimate infeasibility present in the source problem;
- extraction-induced infeasibility;
- solver failure.

### M7 — Decision-quality impact

For each scenario, compare QDIP output from S2 against QDIP output from manual gold S0 using the same evaluation world/reference.

Primary downstream hypothesis:

```text
NR_LLM-Spec <= NR_Manual-Spec + epsilon_semantic
```

where `epsilon_semantic` is pre-registered before the primary test.

If utility/regret is not meaningful for a scenario, use a pre-registered task-specific decision-distance/constraint-outcome metric; do not choose it after seeing results.

This test evaluates semantic preservation through the LLM intake layer, not optimizer superiority.

### M8 — Constraint-violation impact

Report downstream hard-constraint violations caused by semantic extraction errors separately from decision-quality loss.

A system may not trade hard-constraint violations for higher utility.

## 8. Human-effort metric

Measure actual operator/analyst effort for:

- full manual structuring (S0);
- reviewing/correcting S1;
- reviewing/correcting/clarifying S2.

Record person-minutes and correction operations.

Define before freeze:

```text
E_manual
E_naive_review
E_semantic_review
```

Candidate product hypothesis:

```text
E_semantic_review < E_manual
```

Any stronger reduction threshold must be justified and pre-registered before the primary run.

## 9. Failure taxonomy

Every failed case must be assigned one or more categories:

- omitted hard constraint;
- hallucinated hard constraint;
- hard/soft misclassification;
- objective misinterpretation;
- temporal/horizon error;
- unit/quantity error;
- unsupported semantic construct;
- unresolved ambiguity silently resolved;
- contradictory fields;
- invalid action/entity mapping;
- provenance mismatch;
- validator false negative;
- validator false positive;
- downstream infeasibility;
- downstream decision-quality degradation.

Do not discard failed cases from the primary denominator.

## 10. Ablation requirement

The BattleVerse research claim is not supported unless S2 is compared against S1.

Required comparison:

```text
S0 manual gold
vs
S1 naive LLM structured output
vs
S2 LLM + ambiguity/provenance/validation pipeline
```

This isolates the value of the proposed semantic-intake mechanisms from the generic capability of an LLM to emit JSON.

## 11. Statistical design

Before primary execution pre-register:

- sample size;
- scenario stratification;
- primary metric(s);
- confidence intervals;
- paired test/interval method;
- `epsilon_semantic`;
- treatment of abstentions;
- treatment of invalid specs;
- repeated-run policy for stochastic LLM output;
- multiplicity handling if several primary hypotheses are retained.

Do not use "no significant difference" as proof of non-inferiority.

## 12. GO / NO-GO gate for BattleVerse

### GO

Proceed to full BattleVerse application only if the mini-protocol is technically credible and the proposed work contains a falsifiable contribution beyond parsing:

- ambiguity/clarification mechanism;
- constraint/objective semantic extraction;
- deterministic validation;
- provenance/audit;
- downstream decision-impact measurement;
- manual baseline and naive-LLM ablation;
- bounded defence mission-planning demonstrator feasible within six months.

Empirical pilot results are desirable but are not required to claim completed research before the grant. Any unexecuted hypothesis must be presented as proposed work, not existing evidence.

### NO-GO

Stop BattleVerse-specific work if:

- LLM is only a text-to-JSON/parser wrapper;
- no meaningful ambiguity/validation research remains;
- no bounded mission-planning scenario can be defined without classified data;
- the experiment requires replacing QDIP formal authority with free-form LLM reasoning;
- the work forces new defence-specific semantics into QDIP Core solely to fit the call;
- downstream quality/constraint impact cannot be evaluated reproducibly.

## 13. Required evidence artifacts

If GO, the BattleVerse application package should reference or plan to produce:

- frozen scenario set and gold annotations;
- LLM extraction prompt/policy version;
- ambiguity/abstention specification;
- DecisionSpec validator rules;
- failure taxonomy report;
- S0/S1/S2 benchmark results;
- downstream QDIP decision-quality comparison;
- human-effort comparison;
- audit/reproducibility manifest;
- demonstrator architecture and six-month work plan.

## 14. Relationship to canonical QDIP thesis

This experiment does not modify the Universal Runtime thesis.

It adds an application-specific front-end research question:

> Can uncertain natural-language mission intent be compiled into validated formal decision semantics with controlled failure behavior and low downstream decision-quality loss?

The generic QDIP claim remains evaluated by the Canonical Evidence Pack and Test A/B/C.
