---
artifact_type: cross_system_data_ownership
status: example
confidence: medium
---

# Cross-System Data Ownership

| Business Entity | Current System of Record | Physical source examples | Consuming systems | Target ownership hypothesis | Migration note |
|---|---|---|---|---|---|
| Product / Item | RMS | `RMS.ITEM_MASTER` | RPM, BY SRD, ETL, OBIEE | Product Catalogue | Start with read model |
| Supplier | RMS / VendorLink | `RMS.SUPPLIER` | RMS, ReIM, Reporting | Supplier Management | Resolve ownership split |
| Item Supplier Cost | RMS / VendorLink | `RMS.ITEM_SUPPLIER`, `RMS.COST_CHANGE` | RPM, RMS, Reporting | Product Costing or Supplier Costing | High rule risk |
| Price Event | RPM | `RPM.PRICE_EVENT` | Price Engine, ETL | Pricing | Requires product/zone context |
| Promotion | RPM / 1P | `RPM.PROMOTION` | Price Engine, 1P, Reporting | Promotions | High rule complexity |
| Price Zone | RPM | `RPM.PRICE_ZONE`, `RPM.ZONE_LOCATION` | RPM, Price Engine | Price Zone Reference | Good enabling slice |

## Ownership principle

A target service should own writes for an entity only when:

1. Business owner is agreed.
2. All write rules are documented.
3. Downstream contracts are known.
4. Historical/reporting needs are addressed.
