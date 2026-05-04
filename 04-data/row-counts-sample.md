---
artifact_type: row_counts
status: example_values_only
confidence: low
---

# Row Counts — Sample Scale Indicators

> These are illustrative values to show the template. Replace with real read-only database counts.

| System | Table | Entity | Example Row Count | Size Class | Modernization implication |
|---|---|---|---:|---|---|
| RMS | `ITEM_MASTER` | Item | 2,450,000 | Large | Product read model needs scalable indexing |
| RMS | `ITEM_SUPPLIER` | Item supplier cost | 6,800,000 | Large | Cost rules and history need careful modelling |
| RMS | `PURCHASE_ORDER` | PO header | 12,200,000 | Very large | Not a first-slice candidate |
| RMS | `STOCK_LEDGER` | Stock ledger | 980,000,000 | Massive | Avoid full migration initially; use reporting strategy |
| RPM | `PRICE_EVENT` | Price event | 8,500,000 | Large | Event history and audit important |
| RPM | `PROMOTION` | Promotion | 2,100,000 | Large | Complex rules; decompose before modernization |
| RPM | `PRICE_APPROVAL` | Approval history | 14,300,000 | Very large | Audit/archive strategy needed |

## Query pattern

```sql
SELECT '<TABLE_NAME>' AS table_name, COUNT(*) AS row_count FROM <SCHEMA>.<TABLE_NAME>;
```
