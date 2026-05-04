---
domain: pricing-and-promotions
capability: create-regular-price-event
artifact_type: functional_spec
status: example
confidence: low
---

# Functional Spec — Create Regular Price Event

## 1. Purpose

Enable pricing users to create regular price changes for eligible products and locations/zones, route them for approval and publish approved changes to downstream price engines/channels.

## 2. Actors

| Actor | Responsibility |
|---|---|
| Pricing User | Creates price event |
| Pricing Manager | Approves/rejects price event |
| Product Catalogue | Provides product eligibility context |
| Price Engine | Receives approved price feed |

## 3. Main flow

```mermaid
flowchart TD
    A[Create price event draft] --> B[Select item/product]
    B --> C[Validate product active]
    C --> D[Select zone/location]
    D --> E[Validate zone mapping]
    E --> F[Enter price and effective date]
    F --> G[Check overlap/conflict rules]
    G --> H[Submit for approval]
    H --> I[Approve]
    I --> J[Publish to price engine]
```

## 4. Exceptions

| Exception | Behaviour |
|---|---|
| Product inactive | Reject or keep draft with error |
| Invalid zone | Reject line |
| Effective date in past | Reject submission |
| Downstream publish failure | Retry and record audit |

## 5. Modernization implication

A modern pricing service requires dependable product and zone read models before replacing RPM write behaviour.
