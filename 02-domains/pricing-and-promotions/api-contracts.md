---
domain: pricing-and-promotions
artifact_type: api_contracts
status: target_hypothesis
---

## Purpose
Document the target modernization API contract for Pricing & Promotions, derived from legacy RMS/RPM source evidence and target domain decomposition.

# API Contracts — Pricing & Promotions Target Hypothesis

## POST /price-events

```yaml
method: POST
path: /price-events
request:
  productId: string
  zoneId: string
  effectiveDate: date
  newPrice: decimal
  currency: string
response:
  priceEventId: string
  status: Draft | PendingApproval | Approved | Rejected
preconditions:
  - product is active
  - zone is valid
  - effective date is allowed
legacy_mapping:
  priceEventId: RPM.PRICE_EVENT.PRICE_EVENT_ID
  productId: RPM.PRICE_EVENT_ITEM.ITEM_ID
  zoneId: RPM.PRICE_EVENT.ZONE_ID
```

## POST /price-events/{priceEventId}/approve

```yaml
method: POST
path: /price-events/{priceEventId}/approve
request:
  approverId: string
  decision: Approve | Reject
  comment: string
response:
  priceEventId: string
  status: Approved | Rejected
legacy_rules:
  - RPM-BR-001
  - RPM-BR-002
  - RPM-BR-005
```
