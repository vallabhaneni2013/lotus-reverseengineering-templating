---
artifact_type: ai_agent_playbook
status: example
---

# AI Agent Playbook for Modernization

## 1. Rules for AI agents

- Never infer unused status without evidence.
- Never generate a target API without mapping it to legacy screens, tables, rules and integrations.
- Always preserve source-of-record clarity.
- Treat row counts as scale signals for migration and performance design.
- Treat business rules with low confidence as questions, not facts.

## 2. Prompt pattern for generating a target API

```text
Using the context library, generate a target API design for <capability>.
Required inputs:
- system-overview.md
- capability-behaviour.md
- data-model.md
- integration-execution.md
- modernization-summary.md
- security-and-compliance.md
- performance-profile.md
- user-experience.md

Return:
- API endpoints
- request/response schema
- validation rules
- data ownership assumption
- migration/coexistence approach
- open questions
- confidence level
```

## 3. Prompt pattern for identifying modernization thin slices

```text
Using the context library, rank modernization thin slices for <system/domain>.
Score each by business value, data complexity, integration coupling, rule complexity, usage evidence and decommissioning opportunity.
Return a ranked list with evidence and risks.
```

## 4. Required output traceability

```text
Recommendation → Capability → Module → Screen/API/Job → Table/Entity → Business Rule → Integration → Evidence → Confidence
```
