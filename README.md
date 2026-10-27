# Troodon: APT Alias Interoperability Research Framework

**Status:** Early-stage research prototype. The repository currently provides a basic APT naming-record JSON Schema and supporting example material. The provenance-aware interoperability architecture described below is a research objective, **not an implemented capability**.

## Overview

Different cyber threat intelligence (CTI) producers may use different names for an Advanced Persistent Threat (APT) group or related activity. Conversely, superficially similar names do not necessarily identify the same actor or operational activity. Such naming variation complicates cross-source comparison, dataset integration, analysis, and reproducibility.

**Troodon** investigates a vendor-neutral approach to documenting and reconciling APT naming differences. Its longer-term research direction is to represent possible alias correspondences as explicit, evidence-backed and revisable assertions rather than assuming that every name in an alias list is an exact synonym.

Troodon is **not** an attribution authority, a universal naming standard, or a validated system for automatically resolving threat actors. The current repository does **not** establish the truth of any particular attribution or alias relationship.

## What is available now

The implemented data-model artifact is [`schema/apt-schema.json`](schema/apt-schema.json), a JSON Schema Draft-07 definition titled `APT Naming Entry`.

| Property | Required | Schema constraint | Purpose |
| --- | --- | --- | --- |
| `id` | Yes | String matching `^([A-Z]{2})-APT-\d{2,}$` | Identifier following the schema's prescribed pattern |
| `name` | Yes | String | Primary display name |
| `first_seen` | Yes | String with `date` format | Date represented as `YYYY-MM-DD` |
| `aliases` | Yes | Array of strings | Other reported names |
| `description` | No | String | Brief descriptive text |

The schema sets `additionalProperties` to `false`. Consequently, fields for relationship type, evidence source, provenance, confidence, external STIX identifiers, or ATT&CK mappings **cannot be included in records conforming to the current schema**. The `aliases` array is a list of strings, not a set of typed or evidenced relationships.

The presence of an identifier format does not itself guarantee globally unique identifiers, stable identity assignment, cross-vendor agreement, or accurate attribution. Similarly, the schema describes record structure; it does not implement an ingestion pipeline, matching algorithm, external-source synchronization, or an operational CTI service.

### Illustrative schema-shaped record

The following is a **synthetic illustration of the record shape**, not a verified intelligence assertion and not a claim about the contents of the `examples/` directory:

```json
{
  "id": "ZZ-APT-01",
  "name": "Illustrative Group",
  "first_seen": "2024-01-01",
  "aliases": ["Example Alias A", "Example Alias B"],
  "description": "Fictional record used to illustrate the current data model."
}
```

The `ZZ` prefix above is illustrative only; the schema does not define a geographic or attribution interpretation of the two-letter prefix. Validation of `format: date` can depend on the JSON Schema validator's configuration and support for format assertions.

## Intended research architecture — not yet implemented

The proposed framework would extend beyond flat alias lists by making **claims about relationships** first-class research objects. The following concepts describe a research design, not properties supported by the current JSON Schema or completed software features.

### Proposed relationship categories

| Proposed category | Intended interpretation |
| --- | --- |
| `exact-equivalence` | Two labels are assessed, with supporting evidence and clearly stated scope, to denote the same entity. |
| `partial-overlap` | Labels or tracked entities may share some activity, infrastructure, or operational scope without being coextensive. |
| `suspected-association` | A possible correspondence is recorded but remains uncertain and requires corroboration. |

These names are **conceptual categories only**. They are not currently a schema enumeration, API, executable rule set, or validated classification capability. A future implementation would need to define relationship directionality, scope, temporal validity, conflicts, and whether a proposed category applies to names, tracked clusters, or other objects.

### Proposed provenance and confidence

A research extension could associate each mapping assertion with the source and date of the claim, supporting references, any relevant analyst rationale, version history, and an explicitly defined confidence assessment. This would allow competing vendor assessments to coexist without silently merging them.

**None of these provenance or confidence fields exists in the current schema.** Confidence scoring methods, evidence-weighting rules, and adjudication procedures remain research questions; no calibrated confidence or automated inference should be assumed.

### Proposed CTI interoperability

Future work may assess mappings to relevant STIX 2.x objects and ATT&CK identifiers, with careful attention to distinctions among threat actors, intrusion sets, campaigns, and activity clusters. Such mappings would require defined semantics, external identifiers, evidence handling, and conformance tests.

**The current repository does not demonstrate STIX serialization, STIX import/export, ATT&CK synchronization, or tested compatibility with those ecosystems.** References to STIX and ATT&CK here indicate intended evaluation directions, not certifications or supported integrations.

## Research questions and evaluation directions

Potential research questions include:

1. How can conflicting APT naming assertions be represented without erasing source-specific interpretations?
2. Which evidence types are sufficient to justify equivalence, overlap, or suspected association?
3. How should uncertainty, provenance, and changes over time be represented and evaluated?
4. How effectively could a future mapping approach interoperate with STIX- and ATT&CK-based CTI datasets?
5. How can independent researchers reproduce and audit alias-mapping decisions?

Possible future evaluation measures include schema conformance, source traceability, inter-annotator agreement, mapping precision/recall against an explicitly described reference set, and robustness to disputed or changing attributions. **No results or performance claims are asserted here.**

## Repository layout

The following reflects the publicly visible top-level repository entries reviewed on **27 October 2026**:

```text
Troodon-APT-Alias-Interoperability-Framework/
├── README.md
├── CITATION.cff
├── LICENSE
├── schema/
│   └── apt-schema.json
├── examples/
└── docs/
    └── figures/
```

- [`schema/apt-schema.json`](schema/apt-schema.json): the current APT naming-entry JSON Schema.
- [`examples/`](examples/): example material; inspect individual files before treating their contents as validated mappings.
- [`docs/figures/`](docs/figures/): figure assets; this directory alone does not establish an implemented architecture or governance process.
- [`CITATION.cff`](CITATION.cff): repository citation metadata.
- [`LICENSE`](LICENSE): applicable repository licence text.

No `scripts/` directory is listed in the reviewed repository. Architecture, governance, STIX implementation notes, and validation tooling should not be assumed to exist unless subsequently added and documented.

## Use and reproducibility

Researchers may inspect the schema and examples as starting material for APT-name dataset design. For any research derived from this repository:

- Identify the exact repository commit or version examined.
- Report the applicable JSON Schema and validation tooling, including whether date-format assertions were enabled.
- Distinguish source-reported aliases from independently corroborated equivalence claims.
- Record the source, retrieval date, and interpretation of any external CTI material separately; the current schema does not preserve these details.
- Avoid describing conceptual mappings or interoperability as experimentally verified functionality.

The repository does not currently document a complete reproducible pipeline for ingesting, reconciling, adjudicating, or exporting multi-vendor alias mappings.

## Limitations

The present record model stores names and alias strings without a formal evidence or relationship layer. It does not resolve ambiguous identities, encode disagreements, attribute campaigns, or provide temporal histories of mapping assertions. Neither the schema nor the documentation should be taken as evidence that such functionality has been implemented or empirically validated.

## Roadmap (proposed, not committed functionality)

Potential future work includes: specifying a separate mapping-assertion data model; defining provenance and confidence semantics; documenting adjudication and versioning processes; assessing STIX/ATT&CK interoperability; providing validation and example datasets; and evaluating the approach against independently described CTI sources. These are **research directions**, not a promise of delivery or a claim of current support.

## Citation and licence

For citation details, see [`CITATION.cff`](CITATION.cff). For reuse conditions, consult [`LICENSE`](LICENSE). Cite the precise repository version used in any academic work.

## Scope of this README

This README documents the observed prototype status and proposed research direction as of **27 October 2026**. It does not modify or extend the current JSON Schema, sample records, or repository functionality.
