# BattleVerse OC1 — LLM → DecisionSpec Bounded Qualification Protocol

Status: freeze-ready draft pre-registration for internal GO/NO-GO
Scope: application-specific bounded qualification test over the canonical QDIP runtime

## 1. Purpose and claim boundary

Determine whether an LLM-based semantic-intake layer is a genuine research contribution to QDIP rather than a cosmetic parser or chat wrapper.

The test asks whether ambiguous, partially structured mission/scenario text can be transformed into a formally validated `DecisionSpec` with controlled failure behavior, materially lower human structuring effort, and no material downstream decision-quality degradation relative to a manually structured reference.

This is a **bounded qualification test**, not a statistical proof of broad generalization. Five blind semantic scenarios are sufficient for an internal BattleVerse GO/NO-GO decision only. They must not be described as evidence that the approach generalizes to arbitrary defence or operational domains.

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

The work qualifies as research only if it addresses all of the following non-trivial problems:

1. **Ambiguity handling** — distinguish extractable facts from unresolved or conflicting intent.
2. **Constraint extraction** — map natural-language constraints into typed formal constraints without silently changing meaning.
3. **Objective/priority extraction** — distinguish hard requirements, preferences and optimization objectives.
4. **Controlled abstention / clarification** — reject or request clarification when the source text is insufficient for safe formalization.
5. **Semantic validation** — detect contradictions, unsupported constructs, missing mandatory fields and invalid units/domains.
6. **Failure-mode analysis** — characterize omission, hallucination, conflict-resolution and over-specification failures.
7. **Downstream impact** — measure how extraction errors affect feasibility and decision quality after QDIP execution.

A system that merely converts text to JSON without these mechanisms does not satisfy the BattleVerse research-fit gate.

## 3. Experimental systems

### S0 — Manual Gold Structuring

A domain-qualified human converts each scenario into a canonical `DecisionSpec` using the same schema and semantics available to S1/S2.

This is the primary semantic reference.

### S1 — Naive LLM Extraction Ablation

LLM converts scenario text directly to `DecisionSpec`/JSON with schema formatting only.

No explicit ambiguity model, abstention policy or semantic validation beyond structural schema checks.

Purpose: determine whether S2 adds measurable value beyond generic structured output.

### S2 — Proposed LLM Semantic Intake

LLM extraction plus:

- explicit evidence spans/provenance per extracted field;
- ambiguity/conflict labels;
- support classification;
- clarification/abstention policy;
- deterministic schema validation;
- QDIP semantic validation;
- constraint/objective consistency checks;
- failure logging and audit trace.

Only S2 is the proposed BattleVerse contribution.

## 4. Experimental sequence

### Phase D — Development smoke test

Use exactly **one development scenario** to verify that the S0/S1/S2 pipeline, validators, metrics and audit logging execute end-to-end.

The development scenario may be inspected and used to tune prompts, validator rules and implementation details.

Its result is exploratory and is **not admissible** for the BattleVerse GO decision.

### Freeze point

After Phase D, freeze:

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
blind-scenario identifiers/checksums
gold-package checksums
metric definitions
scoring rubric
aggregation formulas
missing-output rules
tie rules
S1-comparison thresholds
GO/NO-GO thresholds
epsilon_semantic
human-effort thresholds
evaluation-world definitions/statistical procedure
```

No tuning against blind outputs is permitted after this point.

### Phase B — Blind bounded qualification test

Run **five heterogeneous blind scenarios** not used for prompt, validator or policy tuning.

The set should span materially different decision structures while remaining unclassified and bounded, for example:

1. constrained logistics/resource allocation;
2. time-critical readiness/recovery planning;
3. multi-objective route/resource planning under uncertainty;
4. competing mission-priority/resource-allocation problem;
5. degraded-information planning requiring clarification/abstention.

A positive development result cannot compensate for failure on the blind set.

## 5. Gold annotation and freeze procedure

Gold `DecisionSpec` packages must be created independently of S1/S2 outputs.

For every blind scenario:

1. **Author A** prepares scenario text and hidden semantic-intent sheet.
2. **Annotator B**, who did not implement S1/S2, independently creates the candidate gold `DecisionSpec` from the scenario text.
3. **Reviewer C** independently reviews it against the text and frozen DecisionSpec semantics.
4. Disagreements are resolved through documented adjudication before any S1/S2 blind run.
5. The final gold package is canonicalized and hashed.
6. Gold hashes are frozen before S1/S2 execution.
7. S1/S2 outputs may not be used to modify gold.

If independent personnel are unavailable, roles may be performed at different times by the same person only if disclosed as a limitation; this is weaker evidence.

Each frozen gold package contains:

- canonical manual `DecisionSpec`;
- accepted alternative interpretations where genuinely ambiguous;
- hard constraints;
- soft constraints/preferences;
- objective terms;
- uncertainty inputs;
- required clarification points;
- unsupported/missing-information markers;
- expected abstention/clarification behavior;
- provenance links to source spans;
- downstream evaluation world/reference.

## 6. Scenario requirements

Across development and blind scenarios cover at least:

- fully specified intent;
- omitted constraint;
- ambiguous deadline/resource statement;
- conflicting constraints;
- soft preference expressed as mandatory;
- implicit objective;
- unsupported request outside current IR semantics;
- inconsistent units/quantities;
- multiple plausible interpretations;
- adversarial/noisy wording.

## 7. Deterministic scoring rubric

### 7.1 Atomic scoring unit

Every scorable semantic item is represented in gold as an atomic record:

```text
item_id
type
criticality
canonical_value_or_allowed_set
source_span
requires_clarification
allowed_alternative_interpretations
```

An extracted item is correct only if type, operator/relation, referenced entities, units and value/allowed range match gold or a frozen accepted alternative.

Partial semantic matches do not receive fractional credit unless a fractional rule is explicitly frozen for that item before execution.

### 7.2 Ambiguity scoring

For every gold ambiguity item:

- `TP`: S2 explicitly flags the same ambiguity or requests an approved clarification;
- `FN`: ambiguity exists in gold but S2 silently resolves it or ignores it;
- `FP`: S2 flags ambiguity where gold marks the statement as unambiguous;
- `TN`: no ambiguity in gold and none is introduced by S2.

`AmbiguityRecall = TP / (TP + FN)`.

If a scenario contains no gold ambiguity items, ambiguity recall for that scenario is `NA`; it is excluded from the ambiguity-recall denominator but the scenario still contributes false-ambiguity counts.

### 7.3 Provenance scoring

For every extracted executable fact/constraint/objective that requires source support:

- provenance is `correct` only if the cited span directly supports the extracted semantic item;
- a span that merely mentions the same entity but does not support the asserted relation/value is incorrect;
- generated semantics with no supporting source span are provenance failures unless gold explicitly permits derived semantics under a frozen derivation rule.

`ProvenanceAccuracy = correct_supported_items / all_items_requiring_provenance`.

### 7.4 Silent-assumption scoring

A **silent assumption** occurs when S1/S2 inserts a semantic value, hard/soft classification, objective priority, temporal interpretation, entity mapping or constraint interpretation that:

1. is not explicitly supported by source text or a frozen allowed derivation rule;
2. is not one of the gold accepted alternatives; and
3. is not surfaced as unresolved ambiguity/clarification/abstention.

`SilentAssumptionRate = silent_assumptions / all_executable_semantic_items_emitted`.

If a system emits zero executable semantic items, the rate is not set to zero; the output is handled under the missing/abstention rules below.

## 8. Missing-output, abstention and invalid-output rules

Rules are frozen before blind execution.

- **Valid justified abstention**: if gold requires clarification/abstention, a matching S2 abstention counts as correct ambiguity handling and does not count as missing output.
- **Unjustified abstention**: if gold is sufficiently specified and S2 abstains, it counts as a failed output for semantic-validity and downstream-quality gates.
- **Malformed/invalid spec**: counts as semantic-invalid and receives worst-case downstream treatment defined below; it is not removed from denominators.
- **Timeout/provider error**: one pre-registered retry is allowed only for transport/provider failure. If the retry fails, the case is a missing output and fails semantic validity for that run.
- **No post-hoc reruns** for undesirable model output.

For downstream NR, an unjustified abstention, malformed spec, or missing output receives the frozen worst admissible normalized loss for that scenario/evaluation world, denoted `NR_fail,i`, defined from the scenario scale before execution. It may not be dropped.

## 9. Primary semantic metrics and aggregation

Let blind scenarios be `i = 1..5`.

### M1 — Field-level extraction correctness

Report precision/recall/F1 separately for:

- state facts;
- actions/candidates;
- hard constraints;
- soft constraints;
- objectives;
- uncertainty parameters;
- temporal/horizon fields.

Macro averages are descriptive only; safety gates use the specific metrics below.

### M2 — Critical constraint preservation

Per scenario:

```text
CCR_i = correctly_preserved_critical_constraints_i /
        all_gold_critical_constraints_i
```

Aggregate:

```text
CCR_micro = sum(correctly_preserved_critical_constraints_i) /
            sum(all_gold_critical_constraints_i)
```

A scenario with zero gold critical constraints has `CCR_i = NA` and is excluded from the CCR denominator.

### M3 — Hallucinated hard constraints

Per scenario count:

```text
HHC_i = number of unsupported hard constraints that survive into the executable validated spec
```

Aggregate is `HHC_total = sum(HHC_i)`.

### M4 — Silent assumptions

Per scenario:

```text
SAR_i = silent_assumptions_i / executable_semantic_items_i
```

Aggregate micro rate:

```text
SAR_micro = sum(silent_assumptions_i) /
            sum(executable_semantic_items_i)
```

### M5 — Semantic validity

Per scenario output is binary after the frozen validation pipeline:

```text
SV_i ∈ {0,1}
```

Aggregate:

```text
SVR = sum(SV_i) / 5
```

### M6 — Provenance correctness

Use the deterministic rubric in §7.3 and report per-scenario and micro aggregate accuracy.

## 10. Downstream QDIP metrics

### M7 — Extraction-induced infeasibility

Distinguish:

- legitimate infeasibility present in source/gold;
- extraction-induced infeasibility;
- solver failure.

Any extraction-induced infeasibility is reported and cannot be discarded.

### M8 — Decision-quality impact

For each scenario `i` and frozen evaluation world `w`:

```text
DeltaNR_iw = NR_S2,iw - NR_S0,iw
```

Frozen semantic margin:

```text
epsilon_semantic = 0.05
```

Two gates apply simultaneously:

**Per-scenario ceiling**

```text
mean_w(DeltaNR_iw) <= 0.05    for every blind scenario i
```

**Aggregate gate**

```text
mean_i,w(DeltaNR_iw) <= 0.05
```

If multiple evaluation worlds permit an interval procedure, the pre-registered upper confidence bound for the aggregate paired difference must also be `<= 0.05`. If the number/structure of worlds does not support a defensible interval, report the aggregate deterministically and do not make a statistical non-inferiority claim beyond the bounded qualification set.

This evaluates semantic preservation, not optimizer superiority.

### M9 — Hard-constraint violations

For every scenario/world:

```text
HCV_iw = extraction-induced downstream hard-constraint violations
```

Any `HCV_iw > 0` is automatic NO-GO.

## 11. Human-effort metric

Record actual person-minutes for:

- `E_manual,i`: full manual S0 structuring;
- `E_naive,i`: review/correction of S1;
- `E_semantic,i`: review/correction/clarification of S2.

Primary total-effort gate:

```text
sum_i(E_semantic,i) <= 0.70 * sum_i(E_manual,i)
```

Thus S2 must reduce total human structuring/review effort by at least 30% across the blind qualification set.

Per-scenario anti-regression cap:

```text
E_semantic,i <= 1.25 * E_manual,i    for every blind scenario i
```

No case may require more than 25% additional human effort than manual structuring.

Medians are reported descriptively only and are not used as the primary gate at `n=5`.

## 12. Exact S2 vs S1 comparison rules

S2 must demonstrate added value over naive structured-output S1. Define improvement/tie/material regression before execution as follows.

### D1 — Critical-constraint recall

```text
Delta_CCR = CCR_micro,S2 - CCR_micro,S1
better:              Delta_CCR >= +0.05
tie:                 -0.05 < Delta_CCR < +0.05
material regression: Delta_CCR <= -0.05
```

### D2 — Hallucinated hard constraints

```text
better:              HHC_total,S2 <= HHC_total,S1 - 1
tie:                 HHC_total,S2 == HHC_total,S1
material regression: HHC_total,S2 > HHC_total,S1
```

S2 independently must satisfy `HHC_total,S2 = 0`.

### D3 — Silent-assumption rate

```text
Delta_SAR = SAR_micro,S1 - SAR_micro,S2
better:              Delta_SAR >= +0.05
tie:                 -0.05 < Delta_SAR < +0.05
material regression: Delta_SAR <= -0.05
```

### D4 — Semantic-validity rate

```text
Delta_SVR = SVR_S2 - SVR_S1
better:              Delta_SVR >= +0.20
tie:                 -0.20 < Delta_SVR < +0.20
material regression: Delta_SVR <= -0.20
```

Because there are five blind scenarios, `0.20` equals one full scenario.

A metric at ceiling for S1 that S2 merely matches is a **tie**, not an improvement. This intentionally prevents GO when the semantic pipeline adds no measurable value beyond S1.

## 13. Pre-registered numeric GO / NO-GO gate

BattleVerse receives **GO** only if all gates G1–G9 pass.

### G1 — Critical constraint recall

```text
CCR_micro,S2 >= 0.95
```

Additionally, for every scenario with critical constraints:

```text
CCR_i,S2 >= 0.90
```

### G2 — Hallucinated hard constraints

```text
HHC_total,S2 = 0
```

### G3 — Silent assumptions

```text
SAR_micro,S2 <= 0.05
```

and no individual scenario may exceed:

```text
SAR_i,S2 <= 0.10
```

### G4 — Downstream hard-constraint violations

```text
HCV_iw = 0 for every scenario/world
```

### G5 — Semantic non-inferiority within bounded set

Both the per-scenario and aggregate NR gates in §10/M8 must pass.

### G6 — Human effort

Both must pass:

```text
sum_i(E_semantic,i) <= 0.70 * sum_i(E_manual,i)
E_semantic,i <= 1.25 * E_manual,i  for every i
```

### G7 — Added research value over S1

Using D1–D4 in §12:

- S2 must be `better` in at least **3 of 4** dimensions;
- S2 must have **zero material regressions** in the remaining dimension;
- ties do not count as improvements.

### G8 — Provenance / ambiguity control

Frozen minimums:

```text
ProvenanceAccuracy_S2 >= 0.95
AmbiguityRecall_S2 >= 0.90
```

These are micro-aggregated over applicable gold items. Unjustified abstentions remain failures under §8.

### G9 — Blind-set integrity

- all five blind cases must be executed;
- no failed/missing case may be removed;
- gold must remain hash-identical to the pre-run freeze;
- no prompt/validator/policy tuning is allowed after the first blind output is produced.

## 14. Automatic NO-GO conditions

BattleVerse-specific application work stops if any of the following occurs:

- S2 wins only on the development scenario but fails the blind bounded qualification test;
- gold changes after inspecting S1/S2 blind outputs;
- LLM is only a text-to-JSON/parser wrapper;
- S2 fails G7 and therefore does not add measurable value over S1;
- a hallucinated hard constraint survives validation;
- an extraction-induced hard-constraint violation occurs;
- per-scenario or aggregate downstream NR gate fails;
- human effort fails either total reduction or per-scenario anti-regression cap;
- no bounded mission-planning scenarios can be defined without classified data;
- the experiment requires replacing QDIP formal authority with free-form LLM reasoning;
- the work forces new defence-specific semantics into QDIP Core solely to fit the call;
- downstream quality/constraint impact cannot be evaluated reproducibly.

## 15. Statistical interpretation

Five blind semantic scenarios do **not** support a generalization claim.

The protocol may use multiple frozen evaluation worlds within each scenario for the downstream decision-quality calculation where scientifically meaningful. Those worlds can support a paired interval for the bounded scenario set, but they do not increase the number of independent semantic scenarios and must not be represented as such.

Therefore reporting language is restricted to:

> S2 passed/failed the pre-registered bounded BattleVerse qualification set.

Do not claim broad semantic generalization from this test.

## 16. GO / NO-GO procedure

1. Run one development scenario and debug the pipeline.
2. Freeze systems, validators, blind scenarios, gold hashes, scoring, aggregation and thresholds.
3. Execute S1/S2 on all five blind scenarios without tuning.
4. Score with the frozen deterministic rubric.
5. Evaluate G1–G9 mechanically.

```text
ALL G1..G9 PASS       → BATTLEVERSE_GO
ANY mandatory gate fails → BATTLEVERSE_NO_GO
```

No qualitative override is allowed after viewing blind results.

## 17. Required evidence artifacts

If GO, retain:

- development scenario marked exploratory;
- frozen blind scenario set/checksums;
- independently created/reviewed gold packages/checksums;
- S1/S2 prompt/policy versions;
- ambiguity/abstention specification;
- DecisionSpec validator rules;
- scoring rubric and aggregation formulas;
- failure taxonomy report;
- S0/S1/S2 blind results;
- downstream QDIP comparison;
- human-effort ledger;
- G1–G9 qualification report;
- audit/reproducibility manifest;
- demonstrator architecture and six-month work plan.

## 18. Relationship to canonical QDIP thesis

This bounded qualification test does not modify or prove the Universal Runtime thesis.

It tests an application-specific front-end research question:

> Can uncertain natural-language mission intent be compiled into validated formal decision semantics with controlled failure behavior, measurable value over naive structured-output extraction, materially reduced human structuring effort, and bounded downstream decision-quality loss?

The generic QDIP claim remains evaluated separately by the Canonical Evidence Pack and Test A/B/C.
