---
domain: product-and-assortment
artifact_type: business_rules
status: example
---

## Purpose
Capture the target domain business rules for Product & Assortment to inform the modern product service design and migration boundary.

# Business Rules — Product & Assortment

| Rule ID | Rule | Source system | Modernization implication |
|---|---|---|---|
| PA-BR-001 | Product must have a valid merchandise hierarchy before approval. | RMS | Target Product service must validate hierarchy. |
| PA-BR-002 | Product must be active before pricing eligibility. | RMS/RPM | Product API must expose status clearly. |
| PA-BR-003 | Product-location relationship controls selling/ranging eligibility. | RMS/BY SRD | Ranging data must be part of product context or linked context. |
| PA-BR-004 | Supplier must be active before primary supplier assignment. | RMS/VendorLink | Supplier status ownership must be clarified. |
