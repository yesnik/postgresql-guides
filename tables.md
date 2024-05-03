# Tables

## Create table

```sql
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  name VARCHAR(255) NOT NULL UNIQUE,
  created_at TIMESTAMP NOT NULL DEFAULT now()
);
```

## Alter table

### Add column

```sql
ALTER TABLE conference ADD slug VARCHAR(255);
```

### Alter column

Add `NOT NULL` constraint:

```sql
ALTER TABLE conference ALTER COLUMN slug SET NOT NULL;
```

Add default value:

```sql
ALTER TABLE comment ALTER state SET DEFAULT 'submitted';
```

Remove default value / drop default value:

```sql
ALTER TABLE comment ALTER state DROP DEFAULT;
```

In Postgres it's [impossible](https://wiki.postgresql.org/wiki/Alter_column_position) to alter column's position within a table.
