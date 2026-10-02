# BattleVerse OC1 — Scorer Verification and Formal Freeze Procedure

Status: required companion to `01-llm-decision-spec-mini-protocol.md`
Scope: implementation integrity only; this document MUST NOT change the conceptual qualification protocol or any G1–G9 threshold.

## 1. Purpose

The bounded qualification protocol is only trustworthy if the scorer, aggregation functions, missing-output handling and mechanical verdict code implement the preregistered definitions exactly.

Therefore BattleVerse cannot enter blind execution until the evaluation implementation passes independent synthetic fixture tests with known expected outputs and the complete preregistration configuration is serialized into an immutable hashed artifact.

## 2. Required implementation components

The qualification implementation must separate at least these pure or independently testable components:

1. atomic semantic-item matcher;
2. ambiguity scorer;
3. provenance scorer;
4. silent-assumption scorer;
5. critical-constraint recall scorer;
6. hallucinated-hard-constraint counter;
7. semantic-validity scorer;
8. downstream `DeltaNR` calculator;
9. human-effort aggregator;
10. S2-vs-S1 D1–D4 comparator;
11. G1–G9 gate evaluator;
12. final mechanical verdict function.

The final verdict code must consume scored/aggregated results and frozen configuration. It must not contain hidden thresholds or grant-specific exceptions outside the preregistration artifact.

## 3. Synthetic fixture requirement

Before the development dry-run is accepted, scorer tests must cover synthetic fixtures where the expected score can be calculated manually.

At minimum include:

### F01 — Exact semantic match

Expected:

- all extracted atomic items correct;
- `CCR = 1.0` where critical constraints exist;
- `HHC = 0`;
- `SAR = 0`;
- semantic validity = `1`;
- provenance accuracy = `1.0`;
- ambiguity metrics unaffected unless ambiguity items are explicitly present.

### F02 — Omitted critical constraint

Gold contains one critical hard constraint omitted by the candidate spec.

Expected:

- corresponding critical-constraint recall decreases exactly by the frozen denominator rule;
- no hallucinated hard constraint is counted merely because a gold constraint was omitted;
- downstream scoring remains separate from semantic omission scoring.

### F03 — Hallucinated executable hard constraint

Candidate contains one unsupported hard constraint that survives validation.

Expected:

- `HHC = 1`;
- provenance for that item fails;
- silent-assumption count increases if the item was inserted without surfaced ambiguity/clarification;
- final G2 evaluation fails for S2.

### F04 — Correct ambiguity detection / justified abstention

Gold marks the input as requiring clarification; candidate detects the ambiguity and abstains or asks an approved clarification.

Expected:

- ambiguity `TP` increments;
- no missing-output penalty;
- no silent assumption;
- downstream worst-case failure penalty is NOT applied solely because the system correctly abstained.

### F05 — Silent resolution of ambiguity

Gold requires clarification; candidate silently selects one unsupported interpretation.

Expected:

- ambiguity `FN` increments;
- silent-assumption count increments;
- the emitted semantics are scored under normal correctness/provenance rules;
- no manual scorer override is permitted.

### F06 — Unjustified abstention

Gold is sufficiently specified; candidate abstains.

Expected:

- semantic validity/output gate treats the case as failed under the frozen rule;
- `NR_fail,i` is used downstream;
- the case stays in all required denominators.

### F07 — Malformed/missing output

Expected:

- semantic invalidity;
- no silent removal from denominator;
- downstream `NR_fail,i` treatment;
- mechanical gates reflect the failed case.

### F08 — S1/S2 tie at ceiling

S1 and S2 both achieve the same ceiling result on a D1–D4 dimension.

Expected:

- classification is `tie`, never `better`.

### F09 — Absolute S2 improvement boundary

Construct cases exactly at each preregistered D1–D4 threshold.

Expected:

- inclusive boundary behaviour exactly matches the protocol (`>=`, `<=`, equality rules);
- one epsilon below/above each boundary is also tested.

### F10 — Human-effort aggregate pass/fail

Provide known per-case times that exercise:

- total S2 effort exactly `0.70 * manual total` → PASS;
- total S2 effort above the threshold by the smallest represented unit → FAIL;
- one case exactly at `1.25 * manual` → PASS;
- one case above the cap → FAIL regardless of aggregate reduction.

### F11 — Per-scenario NR ceiling

Construct five scenario-level `DeltaNR` values where aggregate mean passes but one scenario exceeds `0.05`.

Expected:

- G5 FAILS because aggregate success cannot hide a per-scenario failure.

### F12 — Missing output cannot improve aggregate

Replace a poor real output with a missing output.

Expected:

- frozen `NR_fail,i` applies;
- score cannot improve because of omission/removal.

### F13 — G7 3-of-4 logic

Exercise at least:

- 3 better + 1 tie → PASS;
- 3 better + 1 material regression → FAIL;
- 2 better + 2 tie → FAIL;
- 4 tie → FAIL.

### F14 — Mechanical final verdict

Exercise every single G1–G9 gate as the sole failing gate while all others pass.

Expected:

- every one-gate failure produces `BATTLEVERSE_NO_GO`;
- only all-gates-pass produces `BATTLEVERSE_GO`.

## 4. Fixture integrity

Synthetic fixtures are not tuning data. Their purpose is implementation verification.

For each fixture record:

```text
fixture_id
fixture_version
input_gold
input_candidate_or_aggregates
expected_atomic_scores
expected_aggregates
expected_gate_states
expected_verdict_if_applicable
rationale
```

Expected values must be specified manually before executing the scorer test suite.

A test that derives its expected value by calling the same production scorer is invalid.

## 5. Numeric and aggregation invariants

Tests must explicitly verify:

- denominator-zero / `NA` handling;
- micro vs per-scenario aggregation separation;
- exact boundary inclusivity;
- deterministic rounding policy;
- no threshold comparison after display rounding;
- no dropped invalid/missing cases;
- fixed weighting of evaluation worlds;
- no accidental reweighting by scenario world count unless explicitly frozen;
- stable ordering/canonicalization of scored items where ordering is irrelevant.

All gate comparisons must operate on full stored precision. Formatting/rounding is presentation-only.

## 6. Preregistration artifact

After the development scenario and before blind execution create:

- `battleverse-preregistration.json`
- `battleverse-preregistration.sha256`

The JSON is the source of truth. The hash file contains the SHA256 of the canonical JSON bytes.

Do NOT embed the artifact's own SHA256 inside the hashed JSON payload.

The artifact must contain at least:

```text
protocol_id
protocol_version
freeze_timestamp
qualification_claim_boundary
scenario_set
scenario_checksums
gold_package_checksums
decision_spec_schema_version
canonical_ir_semantic_version
qdip_runtime_commit
solver_config
llm_model_and_version
llm_decoding_config
s1_prompt_hash
s2_prompt_hash
ambiguity_policy_hash
validator_rules_hash
failure_taxonomy_version
scoring_rubric_version
aggregation_spec
missing_output_spec
retry_spec
nr_fail_spec
evaluation_world_spec
human_effort_spec
D1_D4_thresholds
G1_G9_thresholds
epsilon_semantic
scorer_code_commit
scorer_test_fixture_version
scorer_test_status
synthetic_fixture_checksums
execution_environment
```

Any field capable of changing the GO/NO-GO result must be in the artifact or referenced by immutable hash/version.

## 7. Canonical serialization and hashing

Use exactly one canonicalization implementation for both hash generation and pre-run verification.

Required properties:

- UTF-8;
- deterministic key ordering;
- deterministic numeric representation;
- no insignificant whitespace;
- no trailing newline in canonical bytes unless explicitly chosen and tested;
- stable Unicode handling.

Freeze chain:

```text
battleverse-preregistration.json
        ↓ canonical bytes
SHA256
        ↓
battleverse-preregistration.sha256
        ↓
immutable Git commit/tag/ref
```

The blind executor must recompute the hash before execution and hard-abort on mismatch.

## 8. Freeze entry criteria

Formal freeze is allowed only when ALL are true:

- development scenario completed;
- S0/S1/S2 pipeline dry-run completed;
- scorer synthetic fixture suite passes 100%;
- no unresolved discrepancy between manually expected and computed scores;
- all blind scenario IDs/checksums fixed;
- all gold package hashes fixed;
- all prompts/policies/validators fixed;
- all thresholds/config values present in preregistration artifact;
- scorer implementation commit fixed;
- canonical artifact hash verified independently at least once;
- budget/application writing has not influenced qualification thresholds.

## 9. Post-freeze change policy

After formal freeze the original preregistration is immutable.

### Allowed without invalidating frozen run

Only operational actions that do not modify any frozen input, semantic rule, scoring rule, threshold, model configuration, scenario, gold annotation or implementation artifact.

### Bug discovered before blind execution

If a scorer/pipeline bug is found after freeze but before any blind result is inspected:

1. mark the frozen version `SUPERSEDED_BEFORE_EXECUTION`;
2. document the defect;
3. create a new protocol/preregistration version;
4. fix code and tests;
5. regenerate hashes;
6. refreeze;
7. execute only the new version.

The superseded version remains in history.

### Bug discovered after blind execution starts or results are visible

Do NOT rewrite the existing preregistration or result.

1. preserve the original run and verdict as produced under its frozen version;
2. document the bug and affected outputs;
3. mark the run invalid for primary qualification evidence if the defect can affect scoring/verdict;
4. create a new versioned preregistration;
5. rerun the complete blind qualification under the new frozen version if a new primary verdict is required.

Partial selective rescoring or threshold repair is prohibited.

## 10. Audit artifacts

The qualification evidence package must retain:

- canonical preregistration JSON;
- `.sha256` file;
- freeze commit/ref;
- scorer source commit;
- scorer fixture suite and expected values;
- fixture test output;
- pre-run hash verification output;
- blind raw S1/S2 outputs;
- scored atomic records;
- aggregate report;
- G1–G9 gate report;
- mechanical final verdict;
- any superseded/invalidated protocol versions.

## 11. Sequence after this document

The execution order is fixed:

```text
1. development scenario
2. implement/verify S0/S1/S2
3. scorer synthetic fixtures/tests
4. end-to-end pipeline dry-run
5. create preregistration JSON
6. canonicalize + SHA256
7. freeze commit/ref
8. blind 5-scenario bounded qualification
9. mechanical G1–G9 verdict
10. BattleVerse application only if GO
```

No additional conceptual rescue is permitted after blind results are observed.