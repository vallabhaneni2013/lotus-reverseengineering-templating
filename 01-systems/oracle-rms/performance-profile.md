---
system: oracle-rms
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

# Performance and Scalability Context — Oracle RMS

## Purpose
Define NFRs for RMS's merchandising engine to guide scalable rewrite architecture.

## Key Performance Metrics
- **Latency**: Item update jobs take 2-5 minutes for 10k items (evidence: batch logs).
- **Throughput**: Handles 1M item changes/day; peaks during supplier updates (evidence: database metrics).
- **Scalability**: Vertical scaling only; no horizontal for item hierarchies.

## Non-Functional Requirements
- **Availability**: 99.9% uptime for item master (critical for POS integration).
- **Reliability**: Zero data loss in POs; evidence shows rare rollbacks.
- **Scalability**: Support 2x load for future growth; cloud-native design needed.

## Target Recommendations
- Use event-driven architecture for async item publishing; cache supplier data.
- Implement auto-scaling and monitoring.
- Confidence: Medium—based on logs; requires load testing.

## Open Questions
- What are peak load scenarios? (Owner: Performance SME)