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

## 4. Experimental sequence

The GO/NO-GO decision must not be based on a single scenario.

### Phase D — Development smoke test

Use exactly **one development scenario** to verify that the S0/S1/S2 pipeline, validators, metrics and audit logging execute end-to-end.

The development scenario may be inspected and used to tune prompts, validator rules and implementation details.

Its results are **not** admissible for the BattleVerse GO decision.

### Freeze point

After the development smoke test, freeze:

```text
DecisionSpec schema/version
Canonical IR semantic version
S1 prompt/template
S2 prompt/template
ambiguity/abstention policy
validator rules
failure taxonomy
LLM model/version
LLM decoding configuration
QDIP runtime commit
solver configuration
blind-scenario set identifiers/checksums
gold-package checksums
metric definitions
GO/NO-GO thresholds
epsilon_semantic
human-effort threshold
statistical procedure
```

No tuning against blind-scenario outputs is allowed after this point.

### Phase B — Blind confirmatory test

Run **five heterogeneous blind scenarios** that were not used for prompt, validator or policy tuning.

The five scenarios should span materially different decision structures while remaining unclassified and bounded, for example:

1. constrained logistics/resource allocation;
2. time-critical readiness/recovery planning;
3. multi-objective route/resource planning under uncertainty;
4. competing mission-priority/resource-allocation problem;
5. degraded-information planning requiring explicit clarification/abstention.

The scenario set must exercise different combinations of hard constraints, soft preferences, uncertainty, temporal semantics and ambiguity. A positive result on the development scenario cannot compensate for failure on the blind set.

## 5. Gold annotation and freeze procedure

Gold `DecisionSpec` packages must be created independently of S1/S2 outputs.

For every blind scenario:

1. **Author A** prepares the scenario text and hidden semantic intent sheet.
2. **Annotator B**, who did not implement S1/S2, independently produces the candidate gold `DecisionSpec` from the scenario text.
3. **Reviewer C** independently reviews the candidate gold against the scenario text and the frozen DecisionSpec semantics.
4. Disagreements are resolved through documented adjudication before any S1/S2 blind run.
5. The final gold package is canonicalized and hashed.
6. Gold hashes are frozen before S1/S2 execution.
7. S1/S2 outputs may not be used to modify the gold package.

If independent personnel are unavailable, roles may be performed at different times by the same person only if the limitation is disclosed; this is weaker evidence and must be reported explicitly.

For each scenario, the frozen gold package contains:

- canonical manual `DecisionSpec`;
- accepted alternative interpretations where genuinely ambiguous;
- hard constraints;
- soft constraints/preferences;
- objective terms;
- uncertainty inputs;
- required clarification points;
- unsupported/missing information markers;
- expected abstention/clarification behavior;
- provenance links to source text spans;
- downstream evaluation world/reference.

## 6. Dataset / scenario requirements

Across the development and blind scenarios, cover at least these case classes:

- fully specified intent;
- omitted constraint;
- ambiguous deadline/resource statement;
- conflicting constraints;
- soft preference expressed as if mandatory;
- implicit objective;
- unsupported request outside current IR semantics;
- inconsistent units/quantities;
- multiple plausible interpretations;
- adversarial/noisy wording.

Primary blind scenarios must be held out from prompt/policy tuning.

## 7. Primary semantic metrics

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

Critical omissions and hallucinated hard constraints are counted separately because they have asymmetric operational risk.

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

## 8. Downstream QDIP metrics

### M6 — Extraction-induced infeasible-plan rate

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
NR_S2 <= NR_S0 + epsilon_semantic
```

Frozen GO threshold:

```text
epsilon_semantic = 0.05
```

This is a reference-normalized non-inferiority margin and must not be changed after blind results are observed.

This test evaluates semantic preservation through the LLM intake layer, not optimizer superiority.

### M8 — Constraint-violation impact

Report downstream hard-constraint violations caused by semantic extraction errors separately from decision-quality loss.

A system may not trade hard-constraint violations for higher utility.

## 9. Human-effort metric

Measure actual operator/analyst effort for:

- full manual structuring (S0);
- reviewing/correcting S1;
- reviewing/correcting/clarifying S2.

Record person-minutes and correction operations.

Define:

```text
E_manual
E_naive_review
E_semantic_review
```

Frozen materiality threshold for BattleVerse GO:

```text
E_semantic_review <= 0.70 * E_manual
```

That is, S2 must reduce median human structuring/review effort by at least **30%** on the blind scenarios.

Report S1 effort as an ablation; S2 should also outperform S1 on correction effort unless S1 already meets the manual-reduction threshold without violating semantic/safety gates.

## 10. Failure taxonomy

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

## 11. Ablation requirement

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

S2 must show a measurable improvement over S1 on the safety/semantic metrics. Better formatting alone does not count.

## 12. Pre-registered numeric GO / NO-GO gate

BattleVerse receives **GO** only if all of the following hold on the five blind scenarios.

### G1 — Critical constraint recall

```text
CriticalConstraintRecall_S2 >= 0.95
```

and S2 must exceed S1 on critical-constraint recall.

### G2 — Hallucinated hard constraints

```text
HallucinatedHardConstraints_S2 = 0
```

Any unsupported hard constraint entering the validated executable spec is a gate failure.

### G3 — Silent assumptions

```text
SilentAssumptionRate_S2 <= 0.05
```

and S2 must have a lower silent-assumption rate than S1.

### G4 — Downstream hard-constraint violations

```text
HardConstraintViolations_S2 = 0
```

Any downstream hard-constraint violation attributable to semantic extraction is an automatic NO-GO.

### G5 — Semantic non-inferiority

```text
NR_S2 <= NR_S0 + 0.05
```

Use a pre-registered paired interval/non-inferiority procedure across blind scenarios/evaluation worlds. "No significant difference" is not sufficient.

### G6 — Human effort reduction

```text
median(E_semantic_review) <= 0.70 * median(E_manual)
```

The reduction must be achieved without violating G1–G5.

### G7 — S2 research contribution over naive LLM

S2 must outperform S1 on at least **three of these four** paired safety/semantic dimensions, with no material regression on the fourth:

1. critical-constraint recall;
2. hallucinated hard constraints;
3. silent-assumption rate;
4. semantic-validity rate.

A difference limited to JSON/schema formatting does not qualify.

### G8 — Blind-set consistency

All safety-critical gates G2 and G4 must pass **on every individual blind scenario**. Aggregate success cannot hide a catastrophic single-scenario failure.

G1, G3, G5 and G6 are evaluated on the frozen aggregate procedure, with per-scenario values also reported.

## 13. Automatic NO-GO conditions

BattleVerse-specific application work stops if any of the following occurs:

- S2 wins only on the development scenario but fails the blind gate;
- the gold package is changed after inspecting S1/S2 blind outputs;
- LLM is only a text-to-JSON/parser wrapper;
- S2 does not materially outperform S1 on semantic/safety behavior;
- a hallucinated hard constraint survives validation;
- an extraction-induced hard-constraint violation occurs downstream;
- downstream semantic non-inferiority fails;
- human correction effort is not reduced by the frozen materiality threshold;
- no bounded mission-planning scenarios can be defined without classified data;
- the experiment requires replacing QDIP formal authority with free-form LLM reasoning;
- the work forces new defence-specific semantics into QDIP Core solely to fit the call;
- downstream quality/constraint impact cannot be evaluated reproducibly.

## 14. Statistical design

Before blind execution freeze:

- five blind scenario identifiers/checksums;
- scenario stratification;
- per-scenario evaluation-world count;
- confidence intervals;
- paired test/interval method;
- treatment of abstentions;
- treatment of invalid specs;
- repeated-run policy for stochastic LLM output;
- multiplicity handling if multiple statistical hypotheses are retained.

Because five semantic scenarios alone provide limited statistical power, downstream non-inferiority should use multiple frozen evaluation worlds per scenario where the decision problem permits it. The semantic safety gates remain scenario-level and deterministic where possible.

Do not use "no significant difference" as proof of non-inferiority.

## 15. GO / NO-GO decision procedure

### Step 1 — Development

Run the single development scenario, debug the pipeline and finalize the protocol.

### Step 2 — Freeze

Freeze S1/S2, validators, blind scenarios, gold hashes, QDIP runtime, metrics and all thresholds.

### Step 3 — Blind execution

Execute S1 and S2 on the five blind scenarios without tuning.

### Step 4 — Mechanical verdict

Evaluate G1–G8 exactly as frozen.

```text
ALL G1..G8 PASS  → BATTLEVERSE_GO
ANY mandatory gate fails → BATTLEVERSE_NO_GO
```

No qualitative override is allowed after viewing the blind results.

## 16. Required evidence artifacts

If GO, the BattleVerse application package should reference:

- development scenario marked exploratory;
- frozen blind scenario set/checksums;
- independently created and reviewed gold packages/checksums;
- LLM extraction prompt/policy version;
- ambiguity/abstention specification;
- DecisionSpec validator rules;
- failure taxonomy report;
- S0/S1/S2 blind benchmark results;
- downstream QDIP decision-quality comparison;
- human-effort comparison;
- GO/NO-GO gate report;
- audit/reproducibility manifest;
- demonstrator architecture and six-month work plan.

## 17. Relationship to canonical QDIP thesis

This experiment does not modify the Universal Runtime thesis.

It adds an application-specific front-end research question:

> Can uncertain natural-language mission intent be compiled into validated formal decision semantics with controlled failure behavior and low downstream decision-quality loss?

The generic QDIP claim remains evaluated by the Canonical Evidence Pack and Test A/B/C.
