---
system: oracle-rpm
artifact_type: data_model
status: example
confidence: medium
---

## Purpose

Capture Oracle RPM data ownership and entity relationships in a single data-model document to support migration planning and domain modeling.

# Data Model — Oracle RPM

## Data Ownership Matrix

> Row counts are example values only. Replace with production-safe query outputs from read-only DB access.

| Entity | Physical Tables | System of Record | Create | Read | Update | Delete | Consuming Systems | Example Row Count | Growth / Change Rate | Sensitivity | Notes |
|---|---|---|---|---|---|---|---|---:|---|---|---|
| Price Event | `PRICE_EVENT`, `PRICE_EVENT_ITEM` | RPM | RPM UI/API | Price Engine, ETL | RPM | Restricted | Price Engine, POS | 8,500,000 | High | Core pricing transaction |
| Promotion | `PROMOTION`, `PROMO_COMPONENT` | RPM | RPM / 1P | Price Engine, 1P, ETL | RPM | Restricted | 1P, Price Engine | 2,100,000 | High | Promotion setup and components |
| Clearance Event | `CLEARANCE_EVENT`, `CLEARANCE_ITEM` | RPM | RPM | Price Engine | RPM | Restricted | Price Engine | 740,000 | Medium | Clearance markdowns |
| Price Zone | `PRICE_ZONE`, `ZONE_LOCATION` | RPM | RPM | RMS, Price Engine | RPM | Restricted | Price Engine, RMS | 1,200 | Low | Zone/location mapping |
| Approval | `PRICE_APPROVAL` | RPM | RPM workflow | RPM | RPM | Archive | Audit/Reporting | 14,300,000 | High | Workflow history |

## SQL evidence pattern

```sql
SELECT 'PRICE_EVENT' AS table_name, COUNT(*) AS row_count FROM RPM.PRICE_EVENT;
```

## ER Diagram

# ER Diagram — Oracle RPM Pricing & Promotions Core

```mermaid
erDiagram
    PRICE_EVENT ||--o{ PRICE_EVENT_ITEM : contains
    PRICE_EVENT ||--o{ PRICE_APPROVAL : has_approval
    PRICE_EVENT ||--o{ PRICE_PUBLISH_AUDIT : published_as
    PRICE_EVENT ||--o{ ITEM_ELIGIBILITY : targets
    PRICE_EVENT ||--o{ PRICE_ZONE : scoped_by
    PRICE_ZONE ||--o{ ZONE_LOCATION : contains
    PROMOTION ||--o{ PROMO_COMPONENT : composes
    PROMOTION ||--o{ PROMO_ITEM : applies_to
    PROMOTION ||--o{ PRICE_APPROVAL : requires_approval
    CLEARANCE_EVENT ||--o{ CLEARANCE_ITEM : applies_to
    PRICE_ZONE ||--o{ CLEARANCE_EVENT : scoped_by

    PRICE_EVENT {
        string price_event_id PK
        string event_type
        string status
        string product_id
        string zone_id
        date effective_date
        decimal price
    }

    PRICE_EVENT_ITEM {
        string price_event_id FK
        string item_id
        decimal price
    }

    PRICE_APPROVAL {
        string approval_id PK
        string price_event_id FK
        string approver_id
        string approval_status
        date approval_date
    }

    PRICE_PUBLISH_AUDIT {
        string audit_id PK
        string price_event_id FK
        date published_date
        string status
    }

    PRICE_ZONE {
        string zone_id PK
        string zone_name
        string region
    }

    ZONE_LOCATION {
        string zone_id FK
        string location_id
    }

    PROMOTION {
        string promotion_id PK
        string promotion_name
        string status
        date start_date
        date end_date
    }

    PROMO_COMPONENT {
        string promotion_id FK
        string component_type
        string value
    }

    PROMO_ITEM {
        string promotion_id FK
        string item_id
        string reward_type
    }

    CLEARANCE_EVENT {
        string clearance_id PK
        string zone_id FK
        date effective_date
        string status
    }

    CLEARANCE_ITEM {
        string clearance_id FK
        string item_id
        decimal markdown_price
    }
```
