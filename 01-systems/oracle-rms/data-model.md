---
system: oracle-rms
artifact_type: data_model
status: example
confidence: medium
---

## Purpose

Capture Oracle RMS data ownership and entity relationships in a single data-model document to support migration planning and domain modeling.

# Data Model — Oracle RMS

## Data Ownership Matrix

> Row counts are example values only. Replace with production-safe query outputs from read-only DB access.

| Entity | Physical Tables | System of Record | Create | Read | Update | Delete | Consuming Systems | Example Row Count | Growth / Change Rate | Sensitivity | Notes |
|---|---|---|---|---|---|---|---|---:|---|---|---|
| Item | `ITEM_MASTER`, `ITEM_ATTR` | RMS | RMS UI / upload | RPM, BY SRD, ETL, OBIEE | RMS | Restricted | RPM, BY SRD, ETL | 2,450,000 | Medium | Core product entity |
| Supplier | `SUPPLIER`, `SUPPLIER_SITE` | RMS | RMS / VendorLink | RMS, ReIM, OBIEE | RMS / VendorLink | Restricted | ReIM, ETL | 85,000 | Low | Supplier master |
| Item Supplier | `ITEM_SUPPLIER` | RMS | RMS / VendorLink | RPM, RMS, ETL | RMS | Restricted | RPM | 6,800,000 | Medium | Cost and sourcing relationship |
| Location | `LOCATION`, `STORE`, `WAREHOUSE` | RMS | RMS | RPM, BY SRD, ETL | RMS | Restricted | RPM, BY SRD | 4,500 | Low | Store/warehouse/location master |
| Purchase Order | `PURCHASE_ORDER`, `PO_LINE` | RMS | RMS | ReIM, ETL | RMS | Restricted | ReIM | 12,200,000 | High | Transactional |
| Stock Ledger | `STOCK_LEDGER` | RMS | Batch | OBIEE, ETL | Batch | Archive only | OBIEE | 980,000,000 | Very High | Reporting/finance critical |

## SQL evidence pattern

```sql
-- Example safe row-count query pattern
SELECT 'ITEM_MASTER' AS table_name, COUNT(*) AS row_count FROM RMS.ITEM_MASTER;
```

## ER Diagram

# ER Diagram — Oracle RMS Product & Merchandising Core

```mermaid
erDiagram
    ITEM_MASTER ||--o{ ITEM_ATTR : has
    ITEM_MASTER ||--o{ ITEM_SUPPLIER : sourced_by
    SUPPLIER ||--o{ ITEM_SUPPLIER : supplies
    ITEM_MASTER ||--o{ ITEM_LOC : ranged_to
    LOCATION ||--o{ ITEM_LOC : contains
    PURCHASE_ORDER ||--o{ PO_LINE : contains
    ITEM_MASTER ||--o{ PO_LINE : ordered_as
    SUPPLIER ||--o{ PURCHASE_ORDER : receives
    ITEM_MASTER ||--o{ STOCK_LEDGER : posts_movements
    LOCATION ||--o{ STOCK_LEDGER : ledger_location
    ITEM_MASTER ||--o{ COST_CHANGE : cost_changes
    SUPPLIER ||--o{ COST_CHANGE : supplier_cost_change

    ITEM_MASTER {
        string item_id PK
        string item_description
        string item_status
        string department_id
        string class_id
        string subclass_id
        date created_date
        date last_updated
    }

    ITEM_ATTR {
        string item_id FK
        string attribute_name
        string attribute_value
    }

    SUPPLIER {
        string supplier_id PK
        string supplier_name
        string status
        string country
    }

    ITEM_SUPPLIER {
        string item_id FK
        string supplier_id FK
        decimal unit_cost
        string primary_supplier_ind
        date effective_date
    }

    LOCATION {
        string location_id PK
        string location_type
        string region
        string zone_id
    }

    ITEM_LOC {
        string item_id FK
        string location_id FK
        string ranging_status
        date effective_date
    }

    PURCHASE_ORDER {
        string po_id PK
        string supplier_id FK
        string po_status
        date order_date
    }

    PO_LINE {
        string po_id FK
        string item_id FK
        int order_qty
        decimal unit_cost
    }

    STOCK_LEDGER {
        string ledger_id PK
        string item_id FK
        string location_id FK
        string transaction_type
        decimal quantity
        decimal value
        date posting_date
    }

    COST_CHANGE {
        string cost_change_id PK
        string item_id FK
        string supplier_id FK
        decimal old_cost
        decimal new_cost
        date effective_date
    }
```

## AI modernization interpretation

- `ITEM_MASTER` is a candidate aggregate root for a Product Catalogue context.
- `ITEM_SUPPLIER` may belong either in Product Catalogue or Supplier Costing depending on ownership rules.
- `STOCK_LEDGER` is high-volume and should usually not be moved as part of the first thin slice unless required.
