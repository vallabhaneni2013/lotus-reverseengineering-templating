---
domain: pricing-and-promotions
artifact_type: business_rules
status: example
---

## Purpose
Capture the target domain business rules for Pricing & Promotions that will guide the new service design and migration boundary.

# Business Rules — Pricing & Promotions

| Rule ID | Rule | Source system | Modernization implication |
|---|---|---|---|
| PP-BR-001 | Price event requires active product. | RPM/RMS | Pricing service needs Product Catalogue API. |
| PP-BR-002 | Price event requires valid zone/location mapping. | RPM | Price Zone read model needed. |
| PP-BR-003 | Approved price must be published before effective date. | RPM | Publishing reliability and audit required. |
| PP-BR-004 | Promotion overlap rules must be enforced by product/location/date. | RPM | Promotion modernization requires rule extraction. |
