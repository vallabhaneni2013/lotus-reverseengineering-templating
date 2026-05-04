---
artifact_type: architecture_decision_log
status: example
---

# Architecture Decision Log — Example

| Decision ID | Decision | Status | Rationale | Consequence |
|---|---|---|---|---|
| AD-001 | Start with Product Catalogue read model before RMS write replacement | Proposed | Reduces risk and enables downstream modernization | RMS remains source of record initially |
| AD-002 | Build Price Zone read model before Pricing API write replacement | Proposed | Price event validation depends on zone/location context | Adds enabling slice before business-visible pricing write |
| AD-003 | Do not rebuild dormant/deprecated modules without runtime evidence | Proposed | Avoids wasting modernization effort | Requires usage evidence gate |
| AD-004 | Preserve price publish contract during initial pricing strangler | Proposed | Downstream channels depend on stable price feed | Adapter required |
