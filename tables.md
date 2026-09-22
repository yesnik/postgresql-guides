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
