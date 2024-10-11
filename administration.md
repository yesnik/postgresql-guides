# Administration

## Dump

### Create schema dump

```bash
PGPASSWORD=password pg_dump -U username -h hostname -p port -F plain -f db_schema.sql -s dbname
```
- `-s`, `--schema-only` - dump only the schema, no data
- See pg_dump [docs](https://www.postgresql.org/docs/current/app-pgdump.html)

### Create data dump

```bash
PGPASSWORD=password pg_dump -U username -h hostname -p port -F plain -f db_data.sql -a dbname
```

- `-a`, `--data-only` - dump only the data, not the schema

### Import dump

```bash
psql -U username -h hostname -p port -d dbname < db_schema.sql
```
