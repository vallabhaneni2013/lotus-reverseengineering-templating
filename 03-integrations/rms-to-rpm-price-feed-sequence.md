---
integration_id: XINT-001
source: oracle-rms
target: oracle-rpm
artifact_type: sequence_diagram
status: example
---

# RMS to RPM Product Context Feed

```mermaid
sequenceDiagram
    participant RMSDB as RMS DB
    participant RMSJob as RMS_ITEM_EXPORT
    participant SOA as Oracle SOA / Middleware
    participant RPM as RPM Inbound Processor
    participant RPMDB as RPM DB

    RMSJob->>RMSDB: Read changed item/location/cost rows
    RMSDB-->>RMSJob: Changed product context
    RMSJob->>SOA: Send item context feed
    SOA->>RPM: Deliver feed
    RPM->>RPMDB: Upsert item eligibility context
    RPMDB-->>RPM: Commit result
    RPM-->>SOA: Ack/reject records
    SOA-->>RMSJob: Delivery result
```

## Contract fields to validate

| Field | Source | Required by RPM? | Notes |
|---|---|---|---|
| item_id | RMS.ITEM_MASTER | Yes | Product key |
| item_status | RMS.ITEM_MASTER | Yes | Pricing eligibility |
| location_id | RMS.ITEM_LOC | Yes | Zone/location applicability |
| unit_cost | RMS.ITEM_SUPPLIER | Maybe | Margin validation |
| effective_date | RMS item/cost tables | Yes | Price validation |
