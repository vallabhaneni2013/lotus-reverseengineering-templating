---
system: oracle-rpm
artifact_type: ai_modernization_context
status: example
confidence: medium
---

# AI Modernization Context — Oracle RPM

## Purpose

Provide an AI-first summary for Oracle RPM that supports risk-aware modernization planning and target context definition.

This file should help agents understand RPM’s pricing ownership, dependencies on RMS, and candidate delivery slices.

## What AI agents should understand first

1. RPM is the source of record for price events, promotions, clearance, and zone pricing.
2. RPM depends on RMS product, location, and cost context to determine eligibility and pricing logic.
3. Promotions are likely more complex than regular price events because of overlap, precedence, and approval rules.
4. Price publishing is a critical downstream contract with the price engine, POS, and channel systems.

## Recommended AI task sequence

```text
1. Read the RMS product/catalog context in `01-systems/oracle-rms/system-overview.md` before proposing RPM target APIs.
2. Read `01-systems/oracle-rpm/data-model.md` and `01-systems/oracle-rpm/capability-behaviour.md` for RPM price event, promotions, and business rule context.
3. Check integration contracts in `01-systems/oracle-rpm/integration-execution.md` with Price & Promo Engine and downstream consumers.
4. Validate whether read-only price/zone slices can be built before price-write replacement.
5. Do not replace the promotion engine until overlap and precedence rules are fully validated.
```
## Do not assume

- Do not assume price logic is purely standard; Lotus customizations are likely.
- Do not assume promotions can be simplified without rule validation.
- Do not assume downstream publish contracts are replaceable without compatibility checks.
- Do not generate new APIs without confirming the integration contract and business flow.

## Candidate target bounded contexts

| Candidate context | Legacy source | Confidence | Notes |
|---|---|---|---|
| Pricing | Price events, approvals, publishing | Medium | Candidate after product and zone read models are confirmed |
| Promotions | Promotion definitions, components, eligibility | Low/Medium | Higher complexity; decompose carefully |
| Price Zone | Zone mapping, location eligibility, schedule | Medium | Good enabling slice for price execution |
| Price Publishing | Publish jobs and downstream contracts | Low/Medium | May become an adapter/anti-corruption layer |
