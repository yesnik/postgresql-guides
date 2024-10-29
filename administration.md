# Administration

## Create dump

### Schema only

```bash
pg_dump -U username -h hostname -p port -d dbname -s > db_schema.sql
```

- `-s`, `--schema-only` - dump only the schema, no data

### Data only

```bash
pg_dump -U username -h hostname -p port -d dbname -t table1 -t table2 -a > db_data.sql
```

- `-a`, `--data-only` - dump only the data, not the schema
- `-t` - dump only specified tables

Archive dump:

```bash
pg_dump -U username -h hostname -p port -d dbname | gzip > db_data.gz
```

See pg_dump [docs](https://www.postgresql.org/docs/current/app-pgdump.html)

## Import dump

```bash
psql -U username -h hostname -p port -d dbname < db_schema.sql
```

Import from archive:

```bash
gunzip -c db_data.gz | psql -U username -h hostname -p port -d dbname
```

## Remove bloat from tables and indexes

Use tool: [pg_repack](https://github.com/reorg/pg_repack)
