# Users

## Create user

```sql
CREATE USER kenny WITH password '123';

CREATE ROLE developer PASSWORD '123' CREATEDB INHERIT LOGIN;

CREATE ROLE admin PASSWORD '123' SUPERUSER CREATEDB CREATEROLE INHERIT LOGIN;
```

## Drop user

```sql
DROP USER kenny;
```

## Grant all permissions to DB

```sql
GRANT ALL ON DATABASE my_db TO kenny;
```

## Edit user

```sql
ALTER USER kenny INHERIT LOGIN;
```
