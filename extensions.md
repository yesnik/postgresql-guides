# PostgreSQL Extensions

Show extensions and their versions that are available for installation:

```sql
SELECT name, default_version, installed_version FROM pg_available_extensions;
```

To install an extension (in case it does not exist), run the following query:

```sql
CREATE EXTENSION [ IF NOT EXISTS ] extension_name;
```

To upgrade an extension to a newer version, use the following query:
```sql
ALTER EXTENSION extension_name UPDATE TO 'new_version';
```
