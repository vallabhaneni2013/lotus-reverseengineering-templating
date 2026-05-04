---
artifact_type: data_lineage
status: example
confidence: medium
---

# Data Lineage — Product to Price

```mermaid
flowchart LR
    VendorLink[VendorLink supplier/cost terms]
    RMSItem[RMS ITEM_MASTER]
    RMSItemSupplier[RMS ITEM_SUPPLIER]
    RMSItemLoc[RMS ITEM_LOC]
    RPMEvent[RPM PRICE_EVENT]
    RPMLine[RPM PRICE_EVENT_ITEM]
    Engine[Price & Promo Engine]
    POS[POS / Channels]
    Reporting[OBIEE / Reporting]

    VendorLink --> RMSItemSupplier
    RMSItem --> RPMEvent
    RMSItemSupplier --> RPMLine
    RMSItemLoc --> RPMLine
    RPMEvent --> RPMLine
    RPMLine --> Engine
    Engine --> POS
    RMSItem --> Reporting
    RPMEvent --> Reporting
```

## AI interpretation

- Product and cost context flow from RMS into RPM.
- Pricing outputs flow from RPM into downstream price engine and channels.
- Reporting consumes both RMS and RPM, so reporting migration must be planned separately from transactional modernization.
