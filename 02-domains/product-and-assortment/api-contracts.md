---
domain: product-and-assortment
artifact_type: api_contracts
status: target_hypothesis
---

## Purpose
Document the target modernization API contract for Product & Assortment, aligned to legacy RMS source evidence and the new product domain boundary.

# API Contracts — Product & Assortment Target Hypothesis

## GET /products/{productId}

```yaml
method: GET
path: /products/{productId}
response:
  productId: string
  description: string
  status: Draft | Pending | Approved | Inactive
  hierarchy:
    department: string
    class: string
    subclass: string
  attributes:
    - name: string
      value: string
  lastUpdated: datetime
legacy_mapping:
  productId: RMS.ITEM_MASTER.ITEM_ID
  description: RMS.ITEM_MASTER.ITEM_DESCRIPTION
  status: RMS.ITEM_MASTER.ITEM_STATUS
```

## GET /products/{productId}/eligibility/pricing

```yaml
method: GET
path: /products/{productId}/eligibility/pricing
response:
  productId: string
  eligible: boolean
  reasons:
    - code: string
      message: string
legacy_rules:
  - RMS-BR-001
  - RMS-BR-002
  - RPM-BR-001
```
