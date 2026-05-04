---
diagram_type: high_level_block_diagram
status: example
confidence: medium
---

# High-Level Used + Unused Module Block Diagram

## Purpose

Show the module-level delivery posture for Lotus legacy systems, distinguishing active capability from reference-only and candidate decommissioning scope.

This diagram is intended to support prioritization and thin-slice selection by highlighting the areas of the landscape that are:
- actively used and modernization-critical
- passive or read-only
- dormant or obsolete
- unknown and in discovery risk

## Legend

| Status | Meaning |
|---|---|
| Active | Current business/runtime usage identified |
| Passive | Reference or reporting usage only |
| Dormant | Exists but no recent usage evidence |
| Deprecated | Confirmed retired or replaced |
| Unknown | Requires validation and discovery |

## Mermaid diagram

```mermaid
flowchart TB
    subgraph RMS["Oracle RMS - Retail Merchandising System"]
        RMS_ITEM["Item Master\nStatus: Active"]
        RMS_SUP["Supplier Management\nStatus: Active"]
        RMS_PO["PO Management\nStatus: Active"]
        RMS_STOCK["Stock Ledger\nStatus: Passive/Active"]
        RMS_REPL["Replenishment Rules\nStatus: Unknown"]
        RMS_LEGACY_COST["Legacy Cost Upload\nStatus: Dormant"]
    end

    subgraph RPM["Oracle RPM - Retail Price Management"]
        RPM_PRICE["Regular Price Events\nStatus: Active"]
        RPM_PROMO["Promotions\nStatus: Active"]
        RPM_CLEAR["Clearance\nStatus: Active"]
        RPM_ZONE["Zone Pricing\nStatus: Active"]
        RPM_OLD_APPROVAL["Legacy Approval Batch\nStatus: Deprecated"]
    end

    subgraph EXT["External / Extended Landscape"]
        VENDORLINK["VendorLink"]
        BYSRD["BY SRD"]
        ONEP["1P Platform"]
        PRICE_ENGINE["Price & Promo Engine"]
        OBIEE["OBIEE Reporting"]
        ETL["ETL Pipeline"]
    end

    VENDORLINK -->|Supplier terms / cost changes| RMS_SUP
    RMS_ITEM -->|Item master feed| RPM_PRICE
    RMS_ITEM -->|Item-location data| BYSRD
    RPM_PRICE -->|Approved price changes| PRICE_ENGINE
    RPM_PROMO -->|Promotion feed| ONEP
    RMS_STOCK -->|Stock ledger extracts| OBIEE
    RMS_ITEM -->|Batch extract| ETL
    RPM_PRICE -->|Price extract| ETL
```

## Interpretation

- `RMS_ITEM` and `RPM_PRICE` are core seams for modernization, with active usage and strong downstream dependencies.
- `RMS_LEGACY_COST` and `RPM_OLD_APPROVAL` are likely decommissioning candidates, unless evidence proves they are still required.
- `RMS_REPL` is a discovery-risk area; validate its current business role before including it in a modernization slice.
