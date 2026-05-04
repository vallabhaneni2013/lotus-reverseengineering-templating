---
domain: pricing-and-promotions
artifact_type: modernization_notes
status: example
---

## Purpose
Capture the recommended modernization posture, migration strategy, and sequencing guidance for the Pricing & Promotions target domain.

# Modernization Notes — Pricing & Promotions

## Recommended migration posture

Sequence the migration around dependencies:

```mermaid
flowchart TD
    A[Build Product Catalogue Read Model] --> B[Build Price Zone Read Model]
    B --> C[Expose Pricing Read APIs]
    C --> D[Create Price Event API behind RPM adapter]
    D --> E[Modern approval workflow]
    E --> F[Replace price publish job]
```

## Why not start with Promotions?

Promotions are usually rule-heavy: overlap, eligibility, reward mechanics, precedence, dates, channels and supplier funding. Regular price event flow is a better first write candidate after read-model dependencies are in place.
