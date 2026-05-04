---
scope: landscape
status: example
confidence: medium
---

# Lotus Legacy Landscape Overview

## Purpose

Provide a concise, evidence-informed view of Lotus legacy retail systems and the delivery factory used to generate a modernization-ready context library.

This overview is the starting point for understanding system scope, module usage, domain boundaries, and the target deliverables needed to support modernization decisions.

## Delivery factory approach

This repo is built as a delivery factory that converts legacy system knowledge into reusable, AI-readable modernization context:

- Collect stakeholder insights, source code, database objects, and runtime evidence
- Extract capabilities, entities, integrations, and business rules using human review and AI analysis
- Reverse engineer current behavior into system and domain specifications
- Forward engineer an AI-friendly context library with structured markdown, diagrams and evidence links

## Core outcomes

1. **High-level used / unused module diagram**: a system-wide view of active, passive, dormant, and deprecated capability.
2. **Phase 1 — As-is legacy system capture**: system-overview, data-model, capability-behaviour, integration-execution, data ownership, and execution flow documentation. These files describe what exists today and how it behaves.
3. **Phase 2 — To-be target domain design**: domain specs, entity relationships, API contracts, business rules, and modernization-ready target context. These files define what should be built next.
4. **To-be modernization planning**: recommendations, roadmaps, decision logs, and AI-assisted playbooks that turn the target domain design into a practical rewrite sequence.
5. **Evidence support**: `99-evidence` validates both the as-is capture and the to-be recommendations.
## Focus systems

| System | Primary role | Modernization value |
|---|---|---|
| Oracle RMS | Merchandising core: item/master data, suppliers, POs, inventory | Candidate source-of-truth for product and assortment domains |
| Oracle RPM | Pricing engine: price events, promotions, zone pricing, approvals | Candidate source-of-truth for pricing and promotions domains |

## Strategic questions

| Question | Why it matters |
|---|---|
| Which modules are actively used? | Focus modernisation effort on valuable capabilities |
| Which system owns which data? | Avoid duplicate ownership and conflicting semantics |
| Where are integration seams and coupling points? | Define safe strangler and coexistence boundaries |
| What business rules are hidden in legacy implementation? | Preserve critical behaviour during migration |
| Which thin slice delivers value with controlled risk? | Create practical, incremental modernization phases |

## Initial domain map

| Domain | Involved systems | Example core entities |
|---|---|---|
| Product & Assortment | RMS, VendorLink, BY SRD | Item, Supplier, Item Supplier, Location, Assortment |
| Pricing & Promotions | RPM, RMS, 1P, Pricing Engine | Price Event, Promotion, Price Change, Zone, Approval |
| Sales Audit | ReSA, RMS, POS, ETL | Sales Transaction, Store Day, Discount |
| Invoice Matching | ReIM, RMS, AP | Supplier Invoice, PO, Receipt, Match Result |
| Commercial Income | CIS, CAYG, Smartsoft, RMS | Deal, Rebate, Credit Note, Allocation |

## Modernization orientation

This context library enables AI and human teams to identify:

- Candidate bounded contexts and target domain services
- APIs, async event contracts, and data products needed for a modern architecture
- Data ownership and source-of-truth boundaries
- Strangler seams, coexistence patterns, and decommissioning opportunities
- Risks of rebuilding or retiring legacy behavior
