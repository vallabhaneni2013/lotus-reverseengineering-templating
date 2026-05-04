---
domain: product-and-assortment
primary_legacy_system: oracle-rms
artifact_type: domain_spec
status: example
confidence: medium
---

# Domain Spec — Product & Assortment

## 1. Domain purpose

The Product & Assortment domain manages product master data, item attributes, supplier relationships, item-location ranging and the product context required by pricing, replenishment, reporting and downstream channels.

## 2. Business capabilities

| Capability | Description | Legacy systems | Target context hypothesis |
|---|---|---|---|
| Product Master Data | Create and maintain item details | RMS | Product Catalogue |
| Item Attributes | Maintain selling, hierarchy and operational attributes | RMS | Product Catalogue |
| Supplier Association | Link products to suppliers and costs | RMS, VendorLink | Supplier/Product Costing |
| Item-location Ranging | Determine where an item can be sold or stocked | RMS, BY SRD | Assortment Management |

## 3. Core entities

| Entity | Description | System of record | Notes |
|---|---|---|---|
| Item | Sellable or orderable product | RMS | Core aggregate candidate |
| Supplier | Vendor/supplier master | RMS/VendorLink | Ownership to validate |
| Item Supplier | Supplier relationship and cost | RMS | Pricing dependency |
| Location | Store/warehouse/location | RMS | Pricing and assortment dependency |
| Item Location | Ranging relationship | RMS/BY SRD | Ownership to validate |

## 4. Target API candidates

| API | Purpose | Risk |
|---|---|---|
| `GET /products/{itemId}` | Read item context | Low/Medium |
| `GET /products/{itemId}/locations` | Read item-location ranging | Medium |
| `GET /products/{itemId}/suppliers` | Read item supplier/cost context | Medium/High |
| `POST /products` | Create product | High; requires lifecycle rules |

## 5. Domain invariants

- Product must belong to a valid merchandise hierarchy.
- Product must have valid status before pricing and ranging.
- Product-supplier relationship must be active before cost and PO usage.
- Product-location relationship controls eligibility for pricing and downstream selling.
