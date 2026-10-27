# Troodon: Proposed Framework Architecture

**Status: conceptual research design (27 October 2026).** This document describes an intended architecture; it does not assert that the described components exist as software. The current implementation is the basic naming-entry schema at [../schema/apt-schema.json](../schema/apt-schema.json).

## Problem and scope

Threat intelligence publishers may use different labels for partially overlapping actor, intrusion-set, campaign, and activity-cluster concepts. Alias strings alone cannot encode the source-specific meaning, evidence, disagreement, or change over time. Troodon proposes an interoperability overlay rather than a universal attribution registry.

## Existing record model

The existing JSON Schema stores `id`, `name`, `first_seen`, and `aliases`, with optional `description`. Its `additionalProperties: false` prevents relationship assertions, provenance, and confidence from being embedded in those records. Nothing in this document changes that schema.

## Proposed logical components (not implemented)

1. **Source registry:** records publisher, report reference, publication and retrieval dates, and licensing/access restrictions.
2. **Entity mentions:** distinguishes the publisher's original name and its referent (actor, intrusion set, campaign, activity cluster, or unknown) without silently normalising meaning.
3. **Mapping assertions:** preserves the two source-scoped mentions, relationship category, evidence references, analyst rationale, uncertainty, and revision history.
4. **Review and adjudication:** supports conflicting assertions and recording why decisions changed.
5. **Interoperability adapter:** potentially exports traceable statements using applicable STIX 2.x objects, relationship structures, and external references, after semantic compatibility is established.

These are logical design responsibilities, not claims of implemented APIs, pipelines, services, or integrations.

## Proposed relationship vocabulary

- `exact-equivalence`: evidentially supported same referent **within a defined scope and time**; do not infer exact attribution solely from similar names.
- `partial-overlap`: some attributed operations, infrastructure, or tracked activity overlaps but the two referents are not proven coextensive.
- `suspected-association`: possible association with insufficient evidence for equivalence or overlap.

An additional `unrelated` or `insufficient-evidence` annotation may be useful for evaluation; neither is implemented. Relationship directionality, temporal scope, and the semantics of cross-entity-type comparisons require formal specification.

## Proposed evidence and confidence semantics

Each mapping assertion should ideally retain the original claim, a persistent reference and relevant passage or locator, publisher, source date, retrieval date, reviewing analyst, and evidence interpretation. An explicit uncertainty label may be preferable to a numeric confidence score until calibration data and procedures exist. Confidence is *not* a probability unless empirically calibrated. Conflicting assertions should coexist and be resolvable by provenance rather than overwritten.

## Illustrative workflow — not an executable pipeline

1. Collect a permitted public CTI report and capture bibliographic metadata.
2. Extract source-local name mentions and identify the described entity type.
3. Propose a relationship with cited evidence, defined scope, and an uncertainty statement.
4. Obtain independent review where possible; retain disagreement and rationale.
5. Version the assertion when the source or interpretation changes.
6. Optionally assess standards-compatible exchange, including information lost during conversion.

## Interoperability boundaries

STIX 2.1 already offers relationship objects, confidence and external references; ATT&CK offers group objects and associated names. Troodon's *hypothesised* contribution is a structured, evidence-linked review process for alias reconciliation, **not the invention of provenance or relationships themselves**. A future comparative study must show whether Troodon adds value beyond existing representations.

## Non-goals and unverified claims

This repository does not currently implement automatic attribution, canonical name adjudication, report ingestion, relationship scoring, conflict resolution, a REST API, or STIX export. No improvements in mapping accuracy, analyst workload, or scalability have been experimentally demonstrated.

See [METHODOLOGY.md](METHODOLOGY.md) and [LIMITATIONS.md](LIMITATIONS.md).
