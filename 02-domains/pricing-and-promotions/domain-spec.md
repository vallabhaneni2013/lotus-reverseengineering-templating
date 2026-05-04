---
domain: pricing-and-promotions
primary_legacy_system: oracle-rpm
artifact_type: domain_spec
status: example
confidence: medium
---

# Domain Spec — Pricing & Promotions

## 1. Domain purpose

The Pricing & Promotions domain manages regular prices, promotions, clearance events, price zones, approvals and publication of approved prices to downstream selling channels.

## 2. Business capabilities

| Capability | Description | Legacy systems | Target context hypothesis |
|---|---|---|---|
| Regular Pricing | Create, approve and publish base price changes | RPM | Pricing |
| Promotions | Create, approve and publish temporary offers | RPM, 1P | Promotions |
| Clearance | Create and activate clearance markdowns | RPM | Pricing / Clearance |
| Zone Pricing | Maintain price zones and location mapping | RPM | Price Zone Reference |
| Price Publishing | Publish approved prices to downstream engines | RPM, Price Engine | Pricing Publisher / Adapter |

## 3. Core entities

| Entity | Description | System of record | Notes |
|---|---|---|---|
| Price Event | Regular price change event | RPM | Candidate aggregate |
| Promotion | Promotional offer | RPM | More complex than regular price |
| Price Zone | Grouping of locations for price applicability | RPM | Could be reference context |
| Approval | Workflow/audit of price approval | RPM | Requires audit strategy |
| Published Price | Downstream price result | Price Engine/RPM | Ownership to validate |

## 4. Target API candidates

| API | Purpose | Risk |
|---|---|---|
| `GET /price-zones/{zoneId}` | Read zone mapping | Low/Medium |
| `POST /price-events` | Create price event | High |
| `POST /price-events/{id}/approve` | Approve price event | High |
| `GET /price-events/{id}` | Read price event | Medium |

## 5. Domain invariants

- Price event requires valid product and location/zone context.
- Effective dates must be valid and must not violate configured overlap rules.
- Approved price events must be published before effective date.
- Promotion rules may override or interact with regular pricing depending on precedence.
