---
library_name: lotus-ai-ready-context-library-example
version: 0.1.0
status: example
delivery_model: reverse-engineering delivery factory
systems:
  - oracle-rms
  - oracle-rpm
primary_outcome: AI-readable, evidence-backed modernization context for Lotus legacy systems
---

# Context Library Manifest

## 1. Outcome

This library is the modernization delivery outcome: a structured, agent-ready knowledge base that turns legacy system evidence into practical modernization guidance.

It is designed to support:

- System boundary analysis
- Domain and capability modelling
- Data ownership and integration discovery
- Business rules capture
- Complexity assessment
- Thin-slice modernization planning

## 2. Repository map

| Folder | Purpose | Typical output |
|---|---|---|
| `00-landscape` | Cross-system landscape and architecture view | High-level module diagrams, domain map, usage classification |
| `01-systems` | As-is legacy system technical and business context | Consolidated system-overview, data-model, capability-behaviour, integration-execution, modernization-summary, ai-modernization-context, security-and-compliance, user-experience, and performance-profile files |
| `02-domains` | To-be target domain specifications and target context | Domain models, ER diagrams, API contracts, business rules |
| `03-integrations` | As-is cross-system interface analysis | Integration catalogue, endpoint matrix, sequence flows, event contracts |
| `04-data` | As-is data ownership and scale context | Data ownership matrix, row counts, lineage, supporting tables |
| `05-execution` | As-is runtime and orchestration context | Job catalogues, execution flows, scheduler maps, transformation logic |
| `06-modernization` | To-be modernization recommendations and planning | Thin-slice proposals, roadmap, decision log, AI playbook |
| `07-template-catalogue` | Reusable artifacts for future studies | Standardized templates for consistent delivery |
| `99-evidence` | Source evidence for traceability | Screenshots, logs, SQL, interview notes, artifacts |

## As-is vs To-be
This library follows the engagement approach from the proposal:

- **Phase 1 (As-is capture)**: Broad system discovery across legacy systems, capturing current capabilities, data, integrations, and execution behavior.
- **Phase 2 (To-be design)**: Deep domain analysis and forward engineering that produces target domain models, API contracts, business rules, and modernization plans.
- `99-evidence` supports both phases by providing the source artifacts used to validate the as-is capture and the to-be recommendations.

## 3. Metadata contract

Each file should include structured metadata where practical, for example:

```yaml
---
system: oracle-rms
domain: product-and-assortment
capability: item-master
status: active
confidence: medium
validated_by:
  - sme_interview
  - database_schema
source_evidence:
  - code
  - runtime_logs
  - screen_capture
---
```

## 4. Traceability model

Recommendations should map through:

```text
Business capability → screen/API/job → business rule → data object → integration → complexity → modernization recommendation
```

## 5. Key system scopes

| System | Role | Modernization focus |
|---|---|---|
| Oracle RMS | Merchandising and master data | Product & assortment source-of-truth, item lifecycle, supplier data |
| Oracle RPM | Pricing and promotion execution | Price events, promotions, zone pricing, approval workflows |
