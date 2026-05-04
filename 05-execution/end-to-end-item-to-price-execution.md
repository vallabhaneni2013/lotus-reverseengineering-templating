---
artifact_type: execution_sequence
status: example
confidence: medium
---

# End-to-End Execution — Item Creation to Price Publication

```mermaid
sequenceDiagram
    actor Merch as Merchandising User
    actor Pricing as Pricing User
    participant RMS as Oracle RMS
    participant RMSDB as RMS DB
    participant Export as RMS_ITEM_EXPORT
    participant RPM as Oracle RPM
    participant RPMDB as RPM DB
    participant Publish as PRICE_PUBLISH_JOB
    participant Engine as Price & Promo Engine
    participant POS as POS / Channels

    Merch->>RMS: Create/approve item
    RMS->>RMSDB: Save ITEM_MASTER / ITEM_LOC / ITEM_SUPPLIER
    Export->>RMSDB: Read changed product context
    Export->>RPM: Send item/location/cost feed
    RPM->>RPMDB: Store item eligibility context
    Pricing->>RPM: Create price event for item and zone
    RPM->>RPMDB: Save PRICE_EVENT / PRICE_EVENT_ITEM
    Pricing->>RPM: Approve price event
    RPM->>RPMDB: Save approval status
    Publish->>RPMDB: Select approved effective events
    Publish->>Engine: Publish price feed
    Engine->>POS: Make price available to channels
```

## Critical modernization seams

| Seam | Why important |
|---|---|
| RMS item export | Can be replaced by Product Catalogue read model/event |
| RPM price event save | Candidate future Pricing API |
| RPM price publish | Needs adapter until downstream consumers migrate |
