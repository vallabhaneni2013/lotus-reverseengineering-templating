---
system: oracle-rms
artifact_type: ai_modernization_context
status: example
confidence: medium
---

# AI Modernization Context — Oracle RMS

## Purpose

Provide an AI-first summary for Oracle RMS that is aligned to evidence-backed modernization planning and delivery.

This file should help agents understand the system’s source-of-record boundaries, key dependency assumptions, and candidate modernization slices.

## What AI agents should understand first

1. RMS is the assumed source of record for item master, supplier, item-supplier, purchase orders, and core merchandise catalog data.
2. RPM consumes RMS product, location, and cost context to evaluate price and promotion eligibility.
3. The RMS stock ledger is high-volume and high-risk; treat it as a low-priority migration target unless a strong business case exists.
4. Dormant and legacy modules must be validated with runtime evidence before they are considered removable.

## Recommended AI task sequence

```text
1. Read system-overview.md for RMS scope and interfaces.
2. Read capability-behaviour.md to identify legacy capability boundaries.
3. Read data-model.md to verify source-of-truth and data scale.
4. Read integration-execution.md to understand external contracts and coupling.
5. Read modernization-summary.md to validate business rules, recommendations, and risk.
6. Propose modernization options only when they are traceable to evidence.
```

## Do not assume

- Do not assume legacy code paths are unused without evidence.
- Do not assume reporting or historical data models can be removed.
- Do not assume Oracle standard behaviour applies to Lotus-specific customizations.
- Do not generate target APIs before confirming data ownership and business rules.

## Candidate target bounded contexts

| Candidate context | Legacy source | Confidence | Notes |
|---|---|---|---|
| Product Catalogue | Item Master, Item Attributes, Item Location | Medium | Logical read-model thin slice for item/product context |
| Supplier Management | Supplier and supplier site | Low/Medium | Validate overlap with VendorLink ownership |
| Item Costing | Item Supplier, Cost Change, Costing rules | Low | High business risk; requires detailed rule extraction |
| Purchase Order | PO header, PO line, PO lifecycle | Low | Requires review of downstream ReIM and AP dependencies |
