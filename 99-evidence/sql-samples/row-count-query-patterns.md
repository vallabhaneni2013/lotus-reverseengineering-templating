# Row Count Query Patterns

```sql
-- Replace schema/table with approved read-only access.
SELECT 'ITEM_MASTER' AS table_name, COUNT(*) AS row_count FROM RMS.ITEM_MASTER;
SELECT 'PRICE_EVENT' AS table_name, COUNT(*) AS row_count FROM RPM.PRICE_EVENT;
```

## Safety note

Use read-only accounts. Avoid exporting sensitive row-level data unless approved and sanitized.
