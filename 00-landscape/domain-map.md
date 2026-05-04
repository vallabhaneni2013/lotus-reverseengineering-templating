---
diagram_type: domain_map
status: example
confidence: medium
---

# Domain Map

## Domain-to-system matrix

| Domain | RMS | RPM | Primary data owner | Candidate target bounded context |
|---|---:|---:|---|---|
| Product Master Data | Yes | Consumes | RMS | Product Catalogue |
| Supplier Management | Yes | No | RMS | Supplier Management |
| Assortment / Ranging | Yes | Consumes | RMS / BY SRD | Assortment Management |
| Regular Pricing | Consumes | Yes | RPM | Pricing |
| Promotions | Consumes | Yes | RPM | Promotions |
| Zone Pricing | Consumes | Yes | RPM | Price Zones |
| Stock Ledger | Yes | No | RMS | Inventory Ledger / Reporting |

## Mermaid domain relationship diagram

```mermaid
flowchart LR
    Product[Product & Assortment]
    Supplier[Supplier Management]
    Pricing[Pricing & Promotions]
    Zone[Zone & Regional Pricing]
    Inventory[Inventory / Stock Ledger]
    Reporting[Reporting & Analytics]

    Supplier --> Product
    Product --> Pricing
    Product --> Zone
    Product --> Inventory
    Pricing --> Reporting
    Inventory --> Reporting
```

## AI modernization notes

- `Product & Assortment` should be understood before `Pricing & Promotions` because RPM depends on item and location context from RMS.
- `Pricing & Promotions` can be a thin-slice candidate if price event workflow has clear boundaries and manageable integration dependencies.
