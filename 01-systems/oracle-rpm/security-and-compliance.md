---
system: oracle-rpm
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

# Security and Compliance Context — Oracle RPM

## Purpose
Outline security models, compliance requirements, and governance for RPM's pricing and promotions, ensuring the rewrite preserves or enhances controls.

## Key Legacy Security Patterns
- **Authentication**: User-based login via Oracle EBS; no MFA or SSO integrated.
- **Authorization**: Role-based access (e.g., pricing managers for approvals); evidence from audit logs shows manual overrides for promotions.
- **Data Encryption**: In-transit for price publishing; at-rest for sensitive promotion rules (e.g., discounts tied to PII).

## Compliance Requirements
- **Data Privacy**: Price events may include customer-specific promotions—ensure GDPR/CCPA compliance for anonymization.
- **Financial Regulations**: SOX audit trails for price changes and approvals; evidence from compliance reports indicates manual logging.
- **Industry Standards**: PCI DSS for payment-related pricing if integrated with POS.

## Governance Risks for Rewrite
- **Access Control**: Rebuild role-based permissions; risk of over-permissive defaults.
- **Audit Trails**: Implement immutable logs for price events; validate against legacy audit evidence.
- **Open Questions**: How to handle legacy user roles in the new system? (Owner: Security SME)

## Target Recommendations
- Use OAuth2/JWT for authentication; enforce least-privilege for promotion edits.
- Add encryption and masking for promotion data.
- Confidence: Low—requires full audit review before implementation.