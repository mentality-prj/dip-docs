# BattleVerse Development Qualification Implementation

Status: implementation task
Scope: pre-freeze development only
Depends on:
- `01-llm-decision-spec-mini-protocol.md`
- `02-scorer-freeze-verification.md`
- `battleverse-preregistration.schema.json`

## Objective

Implement and dry-run the complete BattleVerse bounded-qualification pipeline without accessing or executing any blind qualification scenarios.

The task ends at a reproducible freeze-ready state. It does **not** include blind execution or application-writing work.

## Hard scope boundary

Allowed work:

```text
development scenario
→ S0 manual gold
→ S1 naive structured-output baseline
→ S2 semantic-intake pipeline
→ scorer / aggregator
→ synthetic fixtures F01–F14
→ end-to-end development dry-run
→ preregistration artifact generation
→ canonical serialization + SHA256
→ freeze commit/ref
```

Explicitly out of scope before freeze:

- executing any blind scenario through S1 or S2;
- reading blind gold annotations while implementing S1/S2;
- tuning prompts/validators/scorer against blind data;
- changing preregistered semantic scoring to improve development-case results;
- BattleVerse application drafting beyond already-approved fit notes;
- budget construction before official Guide for Applicants verification.

## 1. Development scenario

Create exactly one non-classified development scenario whose only purpose is to exercise the full semantic-intake pipeline.

The development scenario may contain ambiguity, hard/soft constraints, temporal semantics, uncertainty and at least one clarification requirement, but no scorer rule may be introduced solely because that scenario exhibits a particular wording or structure.

Every scorer rule must trace to the preregistered protocol semantics, not to the development scenario.

## 2. S0 — Development gold

Produce a manual development `DecisionSpec` using the frozen/current DecisionSpec semantics.

Required artifacts:

- scenario text;
- gold DecisionSpec;
- gold atomic scoring items;
- accepted alternatives;
- required clarification/abstention annotations;
- provenance spans;
- downstream evaluation world/reference.

Development gold is exploratory and must never be mixed with blind gold or cited as qualification evidence.

## 3. S1 — Naive structured-output baseline

Implement the minimal baseline defined by the protocol:

- same LLM family/provider class intended for S2 unless the protocol explicitly freezes otherwise;
- direct scenario text → structured `DecisionSpec`;
- schema formatting only;
- no explicit ambiguity model;
- no abstention/clarification policy beyond generic model behavior;
- no semantic validation beyond structural schema checks.

S1 must remain intentionally simple but not artificially broken.

## 4. S2 — Semantic-intake pipeline

Implement:

- field extraction with source provenance;
- hard/soft constraint classification;
- objective/priority extraction;
- ambiguity/conflict detection;
- controlled clarification/abstention;
- support classification;
- deterministic schema validation;
- QDIP semantic validation;
- consistency checks;
- unsupported-construct detection;
- failure taxonomy logging;
- auditable intermediate representation before Canonical Decision IR compilation.

S2 must not contain development-scenario-specific keywords, case IDs, entity allowlists or handcrafted branches whose sole purpose is to pass the development case.

## 5. Implementation-leakage guard

The following rule is mandatory:

> Implementation may observe only the development scenario. Blind scenarios, blind semantic-intent sheets and blind gold packages are unavailable to S1/S2 implementers until after the freeze artifact and freeze ref exist.

Repository/process controls should make this operationally true where possible, for example:

- blind material maintained outside the implementation branch/repository until freeze;
- encrypted or access-controlled blind artifacts;
- hashes/identifiers exposed before freeze without semantic content;
- separate owner/reviewer for blind gold when feasible.

Any pre-freeze access to blind semantic content must be recorded as protocol contamination and invalidates the bounded qualification run unless a new blind set is created and frozen.

## 6. Scorer / aggregator implementation

Implement scoring strictly from the preregistered rules.

The scorer must not contain logic derived from the observed development outputs except generic bug fixes needed to implement an already-defined rule.

Required behavior includes:

- atomic item matching;
- ambiguity scoring;
- provenance scoring;
- silent-assumption scoring;
- critical-constraint recall;
- hallucinated hard-constraint counting;
- semantic-validity scoring;
- missing/invalid-output worst-case treatment;
- per-scenario NR ceiling;
- aggregate NR gate;
- human-effort total and per-case cap;
- S2-vs-S1 D1–D4 comparisons;
- mechanical G1–G9 verdict.

## 7. Synthetic scorer fixtures F01–F14

All scorer and aggregation behavior must be tested independently of the development scenario.

Fixtures must be synthetic/minimal and constructed from the protocol semantics only.

At minimum cover:

- exact correct extraction;
- omitted critical constraint;
- hallucinated hard constraint;
- silent assumption;
- justified abstention;
- unjustified abstention;
- malformed output;
- provenance mismatch;
- ambiguity TP/FN/FP cases;
- zero-denominator/NA handling;
- S1/S2 tie at ceiling;
- exact threshold boundary pass/fail cases;
- per-scenario NR pass with aggregate fail and vice versa;
- human-effort total gate plus per-case anti-regression failure.

Acceptance criterion:

```text
F01–F14: 100% PASS
```

No blind execution may begin with any failing or skipped fixture.

## 8. Pipeline dry-run

Run the full pipeline on the development scenario only:

```text
scenario
→ S0/S1/S2
→ validation
→ scorer
→ downstream QDIP execution
→ aggregation
→ dry-run verdict object
→ audit manifest
```

The dry-run verdict has no evidentiary value and must be labeled `DEVELOPMENT_ONLY`.

The purpose is to verify interfaces, deterministic scoring, logging, serialization and failure handling.

## 9. Freeze artifact generation

Only after:

- development pipeline works end-to-end;
- F01–F14 = 100% PASS;
- dry-run artifacts are reproducible;
- prompts/model/provider settings are final;
- scorer/aggregator implementation commit is final;
- blind scenario IDs/checksums and gold hashes are available without exposing semantic content;

create:

- `battleverse-preregistration.json` conforming to `battleverse-preregistration.schema.json`;
- canonical serialized bytes;
- `battleverse-preregistration.sha256` containing SHA256 of those canonical bytes;
- freeze commit/ref containing or referencing all frozen implementation/config artifacts.

The JSON must not embed its own SHA256.

## 10. Freeze integrity requirements

Freeze artifact must bind at least:

- protocol version;
- DecisionSpec version;
- Canonical IR semantic version;
- QDIP runtime commit;
- S1 prompt/template hash;
- S2 prompt/template hash;
- LLM model/provider/version/config;
- validator version/hash;
- scorer/aggregator commit/hash;
- fixture suite version/hash;
- blind scenario identifiers/checksums;
- blind gold package hashes;
- all G1–G9 thresholds;
- D1–D4 thresholds;
- epsilon_semantic;
- NR_fail rules;
- human-effort thresholds;
- aggregation formulas;
- retry/missing-output rules;
- evaluation-world definitions;
- canonicalization version.

## 11. Post-freeze rule

After freeze:

- no conceptual threshold/rubric changes;
- no prompt/model/validator/scorer changes in the frozen run;
- no blind-set substitution based on observed results;
- no selective reruns for undesirable outputs.

If a bug is discovered **before** blind execution:

1. mark the old preregistration `SUPERSEDED_BEFORE_EXECUTION`;
2. fix the bug;
3. rerun F01–F14 and development dry-run;
4. create a new versioned preregistration artifact/hash/ref.

If a verdict-affecting bug is discovered **after** blind outputs have been inspected:

- preserve the original run unchanged;
- mark it invalid for primary evidence if the bug affects scoring/verdict;
- fix under a new protocol/preregistration version;
- create a fresh blind qualification set if required to restore blindness;
- never rewrite the historical run.

## 12. Definition of Done

This implementation task is complete only when all are true:

- [ ] one development scenario exists;
- [ ] S0 gold exists;
- [ ] S1 baseline implemented;
- [ ] S2 semantic-intake pipeline implemented;
- [ ] scorer/aggregator implemented from preregistered semantics only;
- [ ] F01–F14 all pass;
- [ ] development dry-run succeeds end-to-end;
- [ ] dry-run artifacts are reproducible;
- [ ] blind scenario semantic content remained inaccessible to S1/S2 implementation;
- [ ] `battleverse-preregistration.json` generated and schema-valid;
- [ ] canonical bytes hashed to `.sha256`;
- [ ] freeze commit/ref created;
- [ ] all frozen hashes/config references recorded;
- [ ] no blind scenario has been executed.

Only then may the bounded qualification phase begin:

```text
5 blind scenarios
→ mechanical G1–G9 evaluation
→ BATTLEVERSE_GO or BATTLEVERSE_NO_GO
```
