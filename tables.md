# Tables

## Alter table

### Add column

```sql
ALTER TABLE conference ADD slug VARCHAR(255);
```

### Alter column

Add not null constraint:

```sql
ALTER TABLE conference ALTER COLUMN slug SET NOT NULL;
```
