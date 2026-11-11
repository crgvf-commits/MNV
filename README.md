# MNV Layered Taxonomy

Machine-readable taxonomy definitions accompanying the paper:

**Toward a Layered Taxonomy for Interoperable Cyber Threat Intelligence Sharing**

This repository provides the machine-readable artifacts used to operationalize
the Minimum Necessary Value (MNV) layered model in a controlled MISP
environment.

The model separates three complementary functions:

1. core incident classification;
2. semantic normalization across heterogeneous taxonomies;
3. complementary operational context.

The artifacts are intended to support inspection and reproduction of the
representation evaluated in the paper.

## Repository Contents

| File | Model component | Purpose |
|---|---|---|
| `mnv-core.json` | Layer 1: Core classificatory area | Represents the stable RSIT-aligned incident-class backbone and classification confidence. |
| `mnv-norm.json` | Layer 2: Normalization area | Represents canonical concepts, source-taxonomy correspondence, and qualified semantic relationships. |
| `mnv-context.json` | Layer 3: Complementary descriptive area | Represents operational attributes such as attack vector, functional impact, information impact, affected sector, attack phase, and recoverability. |

## Layer 1: Core Classification

`mnv-core.json` defines the shared classificatory backbone used by the model.

The namespace contains:

- RSIT-aligned incident classes;
- classification confidence levels.

The implementation includes the recurrent classes identified in the comparative
analysis and also retains the RSIT-aligned `information-content-security` class
used in the data-exposure scenario.

Class definitions and incident semantics are inherited from the referenced
classificatory vocabulary rather than duplicated as separate machine-tag
predicates.


Example:

```text
mnv-core:core-class="malicious-code"
mnv-core:confidence-level="high"
```

## Layer 2: Semantic Normalization

`mnv-norm.json` defines the semantic correspondence between
canonical concepts and source taxonomies.

The namespace contains:

- canonical labels;
- source taxonomy identifiers;
- qualified semantic relationships.

Supported relationships include exact-match, narrower-than,
broader-than, and related-match.

Source labels are maintained as local free-text tags because
they may vary across institutions.

Example:

```text
mnv-norm:canonical-label="ransomware"
mnv-norm:source-taxonomy="RSIT"
mnv-norm:equivalence-type="narrower-than"
```

## Layer 3: Complementary Operational Context

`mnv-context.json` provides additional operational attributes
without modifying the core incident classification.

The namespace contains:

- attack vector;
- functional impact;
- information impact;
- affected sector;
- phase of attack;
- recoverability.

Example:

```text
mnv-context:attack-vector="phishing-email"
mnv-context:functional-impact="service-degradation"
mnv-context:sector-affected="government"
```
