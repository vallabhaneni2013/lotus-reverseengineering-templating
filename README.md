# Lotus AI-Ready Modernization Context Library

> Purpose: A delivery factory for legacy system reverse engineering, structured context creation, and practical modernization planning.

This repository is an example delivery package for creating AI-friendly, evidence-backed modernization context from Lotus legacy retail systems. It is built to support system assessment, domain modeling, integration analysis, and thin-slice decision making.

## What this delivery factory produces

- High-level used + unused module block diagrams
- Per-system consolidated evidence packages for system overview, data model, capability behavior, execution/integration context, security/compliance, user experience, and performance profiles
- System deep dives that include business rules, modernization candidates, and risk assessment
- Domain specifications with entity models, API contracts, and modernized target context
- Thin-slice recommendations and a modernization roadmap for low-risk delivery

## Why this structure works

- **Practical**: Designed for measurable, repeatable system analysis and modernization planning
- **AI-friendly**: Uses consistent markdown, YAML metadata, tables, and diagrams for agent consumption
- **Human-readable**: Written for architects, SMEs, engineers and product owners
- **Traceable**: Encourages evidence mapping from screens, code, databases, jobs and interviews

## Repository structure

| Folder | Purpose |
|---|---|
| `00-landscape` | Cross-system landscape, used/unused module view, domain maps and architecture overview |
| `01-systems` | As-is legacy system context for RMS, RPM and other legacy systems |
| `02-domains` | To-be target domain specifications and reusable target context independent of legacy systems |
| `03-integrations` | As-is cross-system interface and contract capture |
| `04-data` | As-is data ownership, row counts, lineage and scale context |
| `05-execution` | As-is jobs, schedulers, batch flows and execution sequences |
| `06-modernization` | To-be thin-slice recommendations, roadmap, playbook and decision log |
| `07-template-catalogue` | Reusable templates for system profiles, capability maps, data matrices, and more |
| `99-evidence` | Evidence artifacts for traceability: screenshots, logs, SQL, interviews |

## As-is vs To-be
This library intentionally separates legacy capture from future design.

- **As-is**: `01-systems`, `03-integrations`, `04-data`, and `05-execution` document the current landscape, system behavior, data ownership, integration topology, and runtime orchestration.
- **To-be**: `02-domains` and `06-modernization` describe the target domain model, APIs, business rules, and the modernization plan.
- `00-landscape` provides the cross-system context needed to connect as-is capture and to-be design, while `99-evidence` provides the source artifacts that validate both.

## How to use the library

1. Start at `CONTEXT-LIBRARY-MANIFEST.md` to understand the library map and delivery goals.
2. Review `00-landscape` to see the high-level system landscape and module usage classification.
3. Inspect each system package in `01-systems/<system>/system-overview.md`, `01-systems/<system>/data-model.md`, and `01-systems/<system>/capability-behaviour.md`.
4. Use the consolidated `data-model.md` and `capability-behaviour.md` files to identify boundaries and source-of-truth.
5. Review `integration-execution.md` to understand runtime interactions, contracts, and orchestration.
6. Validate business rules and modernization assumptions in `modernization-summary.md` and evidence references across the system package.
7. Use risk and recommendation context in `modernization-summary.md` to prioritize modernization work.
8. Review `security-and-compliance.md`, `user-experience.md`, and `performance-profile.md` for full rewrite architecture requirements.

## Status and confidence conventions

| Status | Meaning |
|---|---|
| Active | Current business or runtime usage confirmed |
| Passive | Reference-only, reporting, or read-only usage |
| Dormant | Exists but no recent evidence of usage |
| Deprecated | Confirmed replaced, retired or obsolete |
| Unknown | Needs validation before planning |

| Confidence | Meaning |
|---|---|
| High | Validated by two or more evidence sources or SME + runtime confirmation |
| Medium | Supported by some evidence, still requires review |
| Low | Inferred by AI or code analysis only, needs SME validation |
