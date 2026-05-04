---
artifact_type: modernization_roadmap
status: example
confidence: medium
---

# Modernization Roadmap — Example

## Phase 0 — Context readiness

| Activity | Output |
|---|---|
| Validate used/unused modules | Evidence-backed usage classification |
| Validate product and pricing rules | Accepted business rules catalogue |
| Confirm data ownership | Data ownership matrix |
| Confirm integration contracts | Integration catalogue and sequence diagrams |

## Phase 1 — Read-model enablement

```mermaid
flowchart LR
    RMS[(RMS)] --> ProductRM[Product Catalogue Read Model]
    RPM[(RPM)] --> ZoneRM[Price Zone Read Model]
    ProductRM --> ProductAPI[Product API]
    ZoneRM --> ZoneAPI[Zone API]
```

## Phase 2 — Pricing write strangler

```mermaid
flowchart LR
    UI[Modern Pricing UI] --> PricingAPI[Pricing API]
    PricingAPI --> ProductAPI[Product API]
    PricingAPI --> ZoneAPI[Zone API]
    PricingAPI --> Adapter[RPM Adapter]
    Adapter --> RPM[(RPM Legacy)]
    RPM --> Engine[Price Engine]
```

## Phase 3 — Contract replacement

Replace legacy publish jobs and direct table dependencies with versioned APIs/events only after consumers are migrated.
