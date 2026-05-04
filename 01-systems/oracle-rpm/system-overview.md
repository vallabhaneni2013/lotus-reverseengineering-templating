---
system: oracle-rpm
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

Provide a consolidated Oracle RPM system overview that combines ownership, technical footprint, capability posture, module classification, and modernization risk.

# System Overview — Oracle RPM

## Executive summary

Oracle RPM is the pricing and promotions engine for Lotus. It owns price events, promotions, clearance, zone pricing, and approval workflows, while depending on RMS for item, location, and cost context.

## Ownership and priority

| Area | Value |
|---|---|
| Business owner | Pricing and Promotions |
| Technical owner | Oracle Retail Platform Team |
| Criticality | Very High |
| Modernization priority | High |
| Source-of-record role | Price events, promotions, clearance, zone pricing |

## Technical profile

| Area | Details |
|---|---|
| Product | Oracle Retail Price Management |
| Database | Oracle schema `RPM` |
| Integration style | Oracle SOA, async event feeds, batch publish, price engine feed, file interfaces |
| UI style | Oracle Retail pricing screens |
| Batch patterns | Price event publish, promotion publish, clearance activation |
| Key consumers | Price & Promo Engine, POS/channels, 1P Platform, ETL |

## Business capabilities supported

| Capability ID | Capability | Domain | Priority | Usage status | Confidence |
|---|---|---|---|---|---|
| RPM-CAP-001 | Create Regular Price Event | Pricing & Promotions | High | Active | Medium |
| RPM-CAP-002 | Approve Price Event | Pricing & Promotions | High | Active | Medium |
| RPM-CAP-003 | Create Promotion | Promotions | High | Active | Medium |
| RPM-CAP-004 | Maintain Clearance | Pricing & Promotions | Medium | Active | Medium |
| RPM-CAP-005 | Maintain Zone Pricing | Zone & Regional Pricing | High | Active | Medium |
| RPM-CAP-006 | Legacy Approval Batch | Pricing Workflow | Medium | Deprecated | Low |

## Module inventory and usage classification

| Module | Description | Status | Size | Complexity | Owner | Evidence | Last Observed Usage | Notes | Confidence |
|---|---|---|---|---|---|---|---|---|---|
| Regular Price Events | Create and execute price changes | Active | Large | High | Pricing | UI, DB, downstream price feed | Current month sample | Strong thin-slice candidate | Medium |
| Promotions | Promotion setup, approval, and activation | Active | Large | High | Promotions | UI, 1P integration, price feed | Current month sample | Complex precedence rules | Medium |
| Clearance | Markdown and clearance pricing | Active | Medium | Medium | Pricing | UI and price engine feed | Current month sample | Related to price changes | Medium |
| Zone Pricing | Zone definition and location mapping | Active | Medium | High | Pricing | Location-zone tables, pricing dependency | Current month sample | Critical lookup domain | Medium |
| Legacy Approval Batch | Old approval mechanism | Deprecated | Small | Medium | Unknown | Replacement workflow indicated | Unknown | Do not rebuild unless validated | Low |

## Key risks and unknowns

| Risk / Unknown | Impact | Recommended next action |
|---|---|---|
| Price calculation rules may be split between RPM and downstream price engine | High | Validate rule ownership and execution chain |
| Item and location eligibility depends on RMS product and location data | High | Define and validate the RMS → RPM contract |
| Promotion overlap and precedence rules may be complex | High | Extract and validate with pricing SMEs |
