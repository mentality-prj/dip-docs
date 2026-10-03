# 10 — TRL Roadmap

Status: active reusable grant module

## Principle

TRL must be evidence-based and call-specific. Do not inflate a software prototype's TRL because individual components are production-quality.

A conservative current description is:

- Core runtime and decision infrastructure: implemented software prototype with extensive automated testing;
- Universal Runtime research thesis: internal multi-domain validation is still incomplete;
- external operational validation: not yet treated as established evidence in this pack.

Therefore the application should claim only the highest TRL supported by the target call's formal definition and the attached evidence.

## Evidence ladder

| Evidence stage | Required evidence | Typical interpretation |
|---|---|---|
| concept/formalization | scientific problem, architecture, IR, methodology | research concept established |
| lab prototype | executable runtime, tests, deterministic replay, internal scenarios | prototype demonstrated in controlled environment |
| cross-domain validation | Test A + Test B + blind Test C | reusable runtime thesis empirically tested |
| relevant-environment pilot | external operational data/workflow, user acceptance, measured outcome | validation in relevant environment |
| operational pilot | live integration, monitoring, fallback, governance, repeated decisions | operational demonstration |

## Grant milestone path

1. complete Test A evidence;
2. complete Test B;
3. execute blind Test C under frozen Core/IR/API;
4. secure at least one non-consortium validation partner/LOI where possible;
5. run bounded relevant-environment pilot;
6. document deployment, auditability, security and outcome feedback;
7. only then claim the corresponding higher TRL.

## Call-specific rule

Every overlay must contain:

- target call TRL definition/source;
- starting TRL with evidence links;
- end TRL target;
- exact deliverables required to justify the transition;
- explicit exclusions where the call's TRL terminology does not map cleanly to software.