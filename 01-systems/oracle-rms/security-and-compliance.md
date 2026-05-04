---
system: oracle-rms
artifact_type: security_and_compliance
status: example
confidence: low
validated_by:
  - sme_interview
  - audit_logs
source_evidence:
  - security_policies
  - compliance_reports
---

# Security and Compliance Context — Oracle RMS

## Purpose
Outline security models, compliance requirements, and governance for RMS's merchandising and master data, ensuring the rewrite preserves or enhances controls.

## Key Legacy Security Patterns
- **Authentication**: User-based login via Oracle EBS; no MFA or SSO integrated.
- **Authorization**: Role-based access (e.g., merchandisers for item master); evidence from audit logs shows manual overrides for suppliers.
- **Data Encryption**: In-transit for item data; at-rest for sensitive supplier contracts (e.g., costs tied to PII).

## Compliance Requirements
- **Data Privacy**: Item and supplier data may include personal info—ensure GDPR/CCPA compliance for anonymization.
- **Financial Regulations**: SOX audit trails for cost changes and POs; evidence from compliance reports indicates manual logging.
- **Industry Standards**: PCI DSS for payment-related costs if integrated with invoices.

## Governance Risks for Rewrite
- **Access Control**: Rebuild role-based permissions; risk of over-permissive defaults.
- **Audit Trails**: Implement immutable logs for item/supplier changes; validate against legacy audit evidence.
- **Open Questions**: How to handle legacy user roles in the new system? (Owner: Security SME)

## Target Recommendations
- Use OAuth2/JWT for authentication; enforce least-privilege for item edits.
- Add encryption and masking for supplier data.
- Confidence: Low—requires full audit review before implementation.