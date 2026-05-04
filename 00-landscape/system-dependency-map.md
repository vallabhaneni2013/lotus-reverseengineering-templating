---
diagram_type: system_dependency_map
status: example
confidence: medium
---

# System Dependency Map

```mermaid
flowchart LR
    VL[VendorLink]
    RMS[Oracle RMS]
    RPM[Oracle RPM]
    BY[BY SRD]
    PE[Price & Promo Engine]
    POS[POS / Channels]
    OBIEE[OBIEE]
    ETL[ETL Pipeline]

    VL -->|Supplier, cost, deal terms| RMS
    RMS -->|Item, supplier, location, cost| RPM
    RMS -->|Item-location ranging| BY
    RPM -->|Approved prices and promotions| PE
    PE -->|Final selling prices| POS
    RMS -->|Merchandising extracts| ETL
    RPM -->|Pricing extracts| ETL
    ETL --> OBIEE
```

## Dependency observations

| Dependency | Coupling | Modernization concern |
|---|---|---|
| RMS → RPM item/cost feed | High | Pricing cannot be safely modernized without stable product master contract. |
| RPM → Price & Promo Engine | Medium/High | Price publication contract must be documented before replacement. |
| RMS/RPM → ETL/OBIEE | Medium | Reporting dependencies may keep legacy tables alive after functional migration. |
