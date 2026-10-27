# Troodon: Research Methodology and Reproducibility Plan

**Status: proposed methodology, not a completed study (27 October 2026).**

## Study objective

Investigate whether explicit, source-linked and revisable alias assertions can represent CTI naming disagreement more faithfully and transparently than untyped alias lists, without assuming a universal naming authority.

## Study design distinction

The current GitHub repository provides a naming-entry schema and descriptive examples. It does **not** provide a documented empirical corpus, executed source-selection protocol, annotation exercise, controlled comparison, or measured results. Illustrations in a manuscript must be called *illustrations*, not experimental validation.

## Proposed document collection protocol

1. Define a date window, target publishers, permitted report types, entity types, and license constraints before collecting records.
2. Select sources using an explicit sampling strategy (e.g., stratified by publisher and ambiguity level), rather than choosing only popular, agreed-upon APT groups.
3. For each retained source record publisher, stable URL or citation, publication date, access date, document version, licence, original actor or cluster label, and relevant evidence passage or locator.
4. Preserve contradictions and unresolved labels; do not turn vendor alias claims automatically into ground-truth equivalence.
5. Maintain a source inventory and documented exclusion reasons. Do not redistribute restricted intelligence or malware samples.

These are **recommended future procedures**; they are not represented as procedures already followed by the authors.

## Proposed annotation protocol

Define the unit of analysis as a *pair of source-scoped entity mentions*. Document precise coding rules for `exact-equivalence`, `partial-overlap`, `suspected-association`, `unrelated`, and `insufficient-evidence`. Include source references, date scope, entity category, rationale and uncertainty. Use two independent annotators for a feasible subset, resolve disagreements transparently, and report agreement statistics and class imbalance. Avoid adjudication using exactly the same alias-list output that is being tested.

## Proposed evaluation

Compare against (a) a naïve shared-name / flattened alias-list baseline, (b) an ATT&CK-associated-name representation under a documented matching policy, and (c) a standards-native STIX representation configured to express equivalent evidence when possible. Report class-specific precision, recall, F1, confusion matrices, abstention behaviour, provenance completeness, conflict preservation and handling of later source updates. Measure analyst time only under a controlled and consistently defined task; quantify runtime only if a working system exists.

Split data by source or temporal window where practicable to reduce information leakage. Report sampling uncertainty and errors rather than inventing performance figures.

## Proposed reproducibility checklist

- Versioned repository commit and schema
- Complete inclusion/exclusion rules and source inventory
- Original references, retrieval dates and permission constraints
- Annotation guidelines, reviewer roles and adjudication log
- Evaluation data and code where legally shareable
- Exact baseline configuration, metrics and split definition
- Negative, disputed and uncertain cases
- Ethical, licensing and attribution caveats

## Current implementation boundary

The existing schema cannot encode evidence, confidence, relationship types or source-local claims, because it explicitly rejects additional fields. No claim that this methodology was executed should be made until scripts, datasets and outputs are actually added.

See [ARCHITECTURE.md](ARCHITECTURE.md) and [LIMITATIONS.md](LIMITATIONS.md).
