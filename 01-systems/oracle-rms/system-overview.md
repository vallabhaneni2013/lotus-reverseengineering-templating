---
system: oracle-rms
artifact_type: system_overview
status: example
confidence: medium
validated_by:
  - pending
source_evidence:
  - code_repository
  - database_schema
  - sme_interview_pending
  - runtime_logs_pending
---

## Purpose

Provide a consolidated system overview for Oracle RMS that combines ownership, technical footprint, capability posture, module classification, and modernization risk.

# System Overview — Oracle RMS

## Executive summary

Oracle RMS is the merchandising core for Lotus. It is the assumed source of record for item master, supplier, item-location, purchase order, and selected stock ledger data.

## Ownership and priority

| Area | Value |
|---|---|
| Business owner | Merchandising Operations |
| Technical owner | Oracle Retail Platform Team |
| Criticality | Very High |
| Modernization priority | High |
| Source-of-record role | Product, supplier, PO, location and stock ledger data |

## Technical profile

| Area | Details |
|---|---|
| Product | Oracle Retail Merchandising System |
| Database | Oracle schema `RMS` |
| Integration style | Oracle SOA, async event feeds, batch extracts, direct DB reads, file interfaces |
| UI style | Oracle Retail UI screens |
| Batch patterns | Nightly and intra-day jobs for extracts, updates and reconciliations |
| Key consumers | RPM, VendorLink, BY SRD, ETL, OBIEE, ReIM |

## Business capabilities supported

| Capability ID | Capability | Domain | Priority | Usage status | Confidence |
|---|---|---|---|---|---|
| RMS-CAP-001 | Maintain Item Master | Product & Assortment | High | Active | Medium |
| RMS-CAP-002 | Maintain Supplier and supplier sites | Supplier Management | High | Active | Medium |
| RMS-CAP-003 | Maintain Item-Supplier-Cost | Product & Assortment | High | Active | Medium |
| RMS-CAP-004 | Create Purchase Order | Procurement / Merchandising | High | Active | Medium |
| RMS-CAP-005 | Maintain Stock Ledger | Inventory / Reporting | Medium | Passive/Active | Low |
| RMS-CAP-006 | Legacy Cost Upload | Cost Management | Medium | Dormant | Low |

## Module inventory and usage classification

| Module | Description | Status | Size | Complexity | Owner | Evidence | Last Observed Usage | Notes | Confidence |
|---|---|---|---|---|---|---|---|---|---|
| Item Master | Item creation, attributes and location assignments | Active | Large | High | Merchandising | DB updates, UI, RPM feed | Current month sample | Strong candidate for product catalog thin slice | Medium |
| Supplier Management | Supplier and supplier-site maintenance | Active | Medium | Medium | Supplier Ops | VendorLink integration, UI | Current month sample | Validate boundary with VendorLink | Medium |
| Purchase Order | PO creation and lifecycle | Active | Medium | Medium | Buying | PO tables, ReIM dependency | Current month sample | Downstream ReIM dependency | Medium |
| Stock Ledger | Stock movements, valuations and reporting feeds | Passive/Active | Large | High | Finance/Inventory | ETL/OBIEE extracts, batch writes | Nightly sample | Validate reporting/finance ownership | Low |
| Replenishment Rules | Replenishment setup | Unknown | Small | Medium | Unknown | Code exists, runtime unclear | Unknown | Requires SME validation | Low |
| Legacy Cost Upload | File-based cost upload and adjustments | Dormant | Small | Medium | Unknown | Legacy job exists, no recent run | Unknown | Candidate retirement | Low |

## Key risks and unknowns

| Risk / Unknown | Impact | Recommended next action |
|---|---|---|
| Stock ledger support is used by reporting and finance, but ownership is unclear | High | Validate with finance and reporting SMEs |
| Item lifecycle rules are likely implemented across UI, DB, and batch | High | Extract rules from code, DB constraints and SME interviews |
| Legacy cost upload may still be used in exception handling | Medium | Validate against logs, tickets, and support artifacts |
