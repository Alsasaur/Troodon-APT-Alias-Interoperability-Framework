# Troodon: Current Limitations and Future Research

**Status as of 27 October 2026.** This file distinguishes what can be inspected today from what remains a research proposal.

## Current implementation

The repository exposes a basic APT naming-entry JSON Schema with `id`, `name`, `first_seen`, `aliases` and optional `description`. The schema rejects additional properties. No runtime reconciliation system, provenance-aware relationship store, confidence scoring, STIX exporter, or source-processing workflow is claimed as implemented.

## Scientific limitations

1. **No demonstrated mapping correctness.** Group examples show representational possibilities, not proof of true equivalence.
2. **No controlled experiments.** There are no repository-based precision/recall, F1, human-effort, inter-annotator-agreement, or scalability results.
3. **No documented reference dataset.** A reproducible, independently annotated corpus and sampling protocol have not been published here.
4. **No formal confidence model.** The interpretation, calibration, and update rules for uncertainty remain unspecified.
5. **No evaluated standards integration.** STIX and ATT&CK alignment remains a prospective design goal; standards already provide relationships, confidence fields and references.
6. **No proven novelty over baselines.** Additional value over existing alias lists, standards-native representations, and entity resolution methods must be tested.
7. **No operational scalability evidence.** Update frequency, source disagreement, entity splits/merges and computational overhead are unmeasured.
8. **CTI epistemic uncertainty.** Vendor names may be scoped differently; public reporting can be incomplete, contradictory, politically influenced, or revised.
9. **Risk of author identification.** Public, author-identifying repositories may breach some double-blind venue policies if linked in anonymised manuscripts.

## Proposed evaluation sequence (not completed)

1. Publish explicit mapping assertion semantics and evidence-linked examples.
2. Independently annotate a small, diverse set of ambiguous and unambiguous cases.
3. Implement a minimal validation and revision workflow without disturbing the original schema.
4. Compare against simple alias matching and the same evidence represented using STIX/ATT&CK where applicable.
5. Evaluate traceability, conflicting claims, measured reconciliation quality and update stability.
6. Expand to multi-source corpora and scalability only if initial evaluation warrants it.

## Responsible publication language

**Appropriate:** 'We propose a provenance-aware alias reconciliation architecture and illustrate the intended representation.'

**Not supported yet:** 'Troodon accurately reconciles APT aliases across vendors'; 'the prototype implements confidence-aware matching'; 'STIX interoperability was validated'; or 'the approach outperforms existing methods.'

A conceptual/design paper may be suitable for a venue explicitly accepting such contributions, but descriptive documentation does not replace evaluation requirements for an experimental research paper.
