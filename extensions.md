# PostgreSQL Extensions

Show extensions and their versions that are available for installation:

```sql
SELECT name, default_version, installed_version FROM pg_available_extensions;
```

To install an extension (e.g. `timescaledb`) in the current database:

```sql
CREATE EXTENSION IF NOT EXISTS timescaledb;
```

To upgrade an extension to a newer version, use the following query:
```sql
ALTER EXTENSION extension_name UPDATE TO 'new_version';
```
