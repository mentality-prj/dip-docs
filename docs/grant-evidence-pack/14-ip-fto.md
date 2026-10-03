# 14 — IP / FTO Module

Status: working grant module; not a legal opinion

## IP boundary

The canonical QDIP asset set includes:

- QDIP Core/runtime source code;
- Canonical Decision IR schema and semantics;
- extension/plugin interfaces;
- benchmark/evidence tooling;
- domain adapters and call-specific applications;
- documentation, test assets and reproducibility artifacts.

Ownership and licensing must be documented per repository/component. Grant-specific work must not silently change the licence or ownership of Core.

## FTO checklist

Before submission or commercial release:

1. generate dependency/SBOM inventory;
2. classify all third-party licences and obligations;
3. identify solver/model/API commercial-use restrictions;
4. identify data-source licence and redistribution restrictions;
5. review names/trademarks and external proprietary formats;
6. search relevant patents/claims for any feature proposed as patentable novelty;
7. document employee/contractor IP assignment for contributed code;
8. document grant-specific foreground/background IP rules;
9. record any open-source publication obligation;
10. obtain legal review where a call or customer contract creates material IP exposure.

## Grant rule

The grant application may describe the architecture and research thesis without disclosing source code beyond what the call requires. If a programme requires open-source delivery, prefer an open grant-specific adapter/application over compulsory publication of unrelated Core, subject to the official agreement and legal review.

Do not claim formal freedom-to-operate until an appropriate legal review has been completed.