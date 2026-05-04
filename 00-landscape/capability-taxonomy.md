---
artifact_type: capability_taxonomy
status: example
---

# Capability Taxonomy

## Capability levels

| Level | Description | Example |
|---|---|---|
| L0 | Domain | Product & Assortment |
| L1 | Business capability | Manage product master |
| L2 | Functional capability | Create item, maintain item supplier, approve item |
| L3 | Execution element | Screen, endpoint, batch job, stored procedure |

## Example taxonomy

| L0 Domain | L1 Capability | L2 Capability | L3 Elements |
|---|---|---|---|
| Product & Assortment | Product Master Data | Create and maintain item | Screen: `ITEM_MAINT`; Table: `ITEM_MASTER`; API: `GET /items/{id}` |
| Product & Assortment | Supplier Management | Maintain supplier cost | Screen: `SUP_COST`; Table: `ITEM_SUPPLIER`; Job: `COST_SYNC_JOB` |
| Pricing & Promotions | Regular Pricing | Create regular price event | Screen: `PRICE_EVENT`; Table: `PRICE_EVENT`; API: `POST /price-events` |
| Pricing & Promotions | Promotions | Approve promotion | Screen: `PROMO_APPROVAL`; Table: `PROMOTION`; Job: `PROMO_PUBLISH_JOB` |
