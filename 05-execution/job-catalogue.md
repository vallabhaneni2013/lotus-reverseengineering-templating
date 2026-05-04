---
artifact_type: cross_system_job_catalogue
status: example
confidence: low
---

# Cross-System Job Catalogue

| Job ID | System | Job | Purpose | Input | Output | Dependency | Status | Modernization action |
|---|---|---|---|---|---|---|---|---|
| JOB-001 | RMS | `RMS_ITEM_EXPORT` | Publish item/location/cost context | RMS tables | Feed to RPM/BY SRD | RMS DB, SOA | Active | Preserve/replace with product events/read model |
| JOB-002 | RMS | `COST_SYNC_JOB` | Process supplier cost changes | VendorLink feed | Cost updates | VendorLink | Active | Validate for Supplier Costing API |
| JOB-003 | RPM | `PRICE_PUBLISH_JOB` | Publish approved prices | RPM price tables | Price Engine feed | RPM DB, Engine | Active | Build adapter/publisher |
| JOB-004 | RPM | `PROMO_PUBLISH_JOB` | Publish promotions | RPM promo tables | Promo feed | 1P/Engine | Active | Defer until promo rules understood |
| JOB-005 | RMS/RPM | Reporting extracts | BI extracts | RMS/RPM tables | OBIEE/warehouse | ETL | Active | Create reporting coexistence strategy |
