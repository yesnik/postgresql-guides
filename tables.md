# Tables

## Create table

```sql
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  name VARCHAR(255) NOT NULL UNIQUE,
  created_at TIMESTAMP NOT NULL DEFAULT now()
);
```

### Create table in the tablespace

A [tablespace](https://www.postgresql.org/docs/current/sql-createtablespace.html) allows superusers to define an alternative location on the file system where the data files containing database objects (such as tables and indexes) can reside.

```sql
CREATE TABLESPACE dbspace LOCATION '/data/dbs';

CREATE TABLE mytable (id SERIAL PRIMARY KEY) TABLESPACE dbspace;
```

## Alter table

### Add column

```sql
ALTER TABLE conference ADD slug VARCHAR(255);
```

### Alter column

#### Add `NOT NULL` constraint

```sql
ALTER TABLE conference ALTER COLUMN slug SET NOT NULL;
```

#### Add default value

```sql
ALTER TABLE comment ALTER state SET DEFAULT 'submitted';
```

#### Remove default value / drop default value

```sql
ALTER TABLE comment ALTER state DROP DEFAULT;
```

#### Change column's type

```sql
ALTER TABLE blog ALTER description TYPE TEXT;
ALTER TABLE blog ALTER description TYPE VARCHAR(255);
```

In Postgres it's [impossible](https://wiki.postgresql.org/wiki/Alter_column_position) to alter column's position within a table.

## System Columns

Every table has several [system columns](https://www.postgresql.org/docs/current/ddl-system-columns.html) that are implicitly defined by the system. 

- `tableoid` - The OID of the table containing this row. This column is particularly handy for queries that select from partitioned tables or inheritance hierarchies, since without it, it's difficult to tell which individual table a row came from. The `tableoid` can be joined against the `oid` column of `pg_class` to obtain the table name.
- `xmin` - The identity (transaction ID) of the inserting transaction for this row version. (A row version is an individual state of a row; each update of a row creates a new row version for the same logical row.)
- `cmin` - The command identifier (starting at zero) within the inserting transaction.
- `xmax` - The identity (transaction ID) of the deleting transaction, or zero for an undeleted row version.
  It's possible for this column to be nonzero in a visible row version. That usually indicates that the deleting transaction hasn't committed yet, or that an attempted deletion was rolled back.
- `cmax` - The command identifier within the deleting transaction, or zero.
- `ctid` - The physical location of the row version within its table. Note that although the `ctid` can be used to locate the row version very quickly, a row's `ctid` will change if it is updated or moved by `VACUUM FULL`.
  Therefore `ctid` should not be used as a row identifier. A primary key should be used to identify logical rows.
