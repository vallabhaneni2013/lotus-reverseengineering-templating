---
artifact_type: cross_system_integration_catalogue
status: example
confidence: medium
---

# Cross-System Integration Catalogue

| ID | Source | Target | Payload | Mechanism | Frequency | Business capability | Modernization concern |
|---|---|---|---|---|---|---|---|
| XINT-001 | RMS | RPM | Item, location, cost, status | SOA/batch/API | Scheduled/near real-time | Pricing eligibility | Contract must be stable before pricing modernization |
| XINT-002 | RPM | Price & Promo Engine | Approved prices/promotions | SOA/batch/API | Effective-date driven | Price publication | Adapter may be needed during strangler |
| XINT-003 | VendorLink | RMS | Supplier and cost terms | API/batch | Daily/event-like | Supplier cost updates | Ownership split must be resolved |
| XINT-004 | RMS | BY SRD | Item-location ranging | SOA/batch | Daily | Assortment/ranging | Determine ownership of ranging |
| XINT-005 | RMS/RPM | ETL/OBIEE | Reporting extracts | ETL/direct DB | Nightly | Reporting | Reporting can keep legacy DB dependency alive |

## Integration modernization principles

- Preserve existing outbound contracts during early strangler phases.
- Introduce anti-corruption adapters where legacy data shape differs from target domain model.
- Track every integration with owner, failure behaviour, replay strategy and data contract.
