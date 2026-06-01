# Troodon: A Provenance-Aware APT Alias Interoperability Framework

Troodon is a research prototype for provenance-aware Advanced Persistent Threat (APT) alias reconciliation across heterogeneous cyber threat intelligence (CTI) ecosystems.

It does not impose a universal naming standard and does not perform definitive attribution. Instead, it provides a vendor-neutral interoperability layer for representing, revising, and tracing alias relationships while preserving provenance, confidence, and analytical context.

## Research Purpose

APT groups are often referenced under different names by different vendors, public repositories, and members of the cybersecurity community. For example, a single threat actor may be associated with multiple labels across Microsoft, CrowdStrike, Mandiant, MITRE ATT&CK, and other CTI sources.

Troodon addresses this interoperability problem by modelling alias relationships as structured, evidence-backed, and revisable assertions rather than flat synonym lists.

## Key Features

- Stable canonical identifiers for cross-system referencing
- Typed alias relationships
- Provenance-aware mapping records
- Confidence annotations
- Separation between threat actors, intrusion sets, campaigns, and activity clusters
- Compatibility with STIX and ATT&CK-aligned CTI workflows
- Example JSON records for APT alias reconciliation
- Research prototype suitable for future extension and evaluation

## Relationship Types

Troodon currently supports three primary alias relationship categories:

| Relationship Type | Meaning |
|---|---|
| `exact-equivalence` | Two aliases are treated as referring to the same operational entity with high confidence. |
| `partial-overlap` | Two entities share operational, behavioural, or infrastructure characteristics but may not fully correspond. |
| `suspected-association` | A relationship has been reported or inferred but remains uncertain or weakly evidenced. |

## Repository Structure

```text
schema/      JSON Schema definition for Troodon records
examples/    Example APT alias mapping records
docs/        Framework architecture, governance, and STIX compatibility notes
scripts/     Optional validation scripts

## Troodon Registry Workflow

The Troodon Registry reconciles heterogeneous APT aliases from vendor, public, and community CTI sources into a canonical CTI record while preserving aliases, provenance, and interoperability.

The LaTeX/TikZ source for the workflow figure is available at:

`docs/figures/troodon-registry-workflow.tex`
