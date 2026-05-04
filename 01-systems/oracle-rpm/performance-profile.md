---
system: oracle-rpm
artifact_type: performance_profile
status: example
confidence: medium
validated_by:
  - runtime_logs
  - performance_tests
source_evidence:
  - batch_job_logs
  - database_metrics
---

# Performance and Scalability Context — Oracle RPM

## Purpose
Define NFRs for RPM's pricing engine to guide scalable rewrite architecture.

## Key Performance Metrics
- **Latency**: Price publishing jobs take 2-5 minutes for 10k events (evidence: batch logs).
- **Throughput**: Handles 1M price updates/day; peaks during promotions (evidence: database metrics).
- **Scalability**: Vertical scaling only; no horizontal for zone calculations.

## Non-Functional Requirements
- **Availability**: 99.9% uptime for price publishing (critical for POS integration).
- **Reliability**: Zero data loss in approvals; evidence shows rare rollbacks.
- **Scalability**: Support 2x load for future growth; cloud-native design needed.

## Target Recommendations
- Use event-driven architecture for async publishing; cache zone data.
- Implement auto-scaling and monitoring.
- Confidence: Medium—based on logs; requires load testing.

## Open Questions
- What are peak load scenarios? (Owner: Performance SME)