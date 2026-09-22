# Users

## Create user

```sql
CREATE USER kenny WITH password '123';
```
Create an account where the user can create databases:
```sql
CREATE USER developer PASSWORD '123' CREATEDB;
```
Create an account where the user can create roles:
```sql
CREATE USER admin PASSWORD '123' SUPERUSER CREATEDB CREATEROLE;
```

## Drop user

```sql
DROP USER kenny;
```

## Create role

[CREATE ROLE](https://www.postgresql.org/docs/current/sql-createrole.html) adds a new role to a PostgreSQL database cluster. 

- A role is an entity that can own database objects and have database privileges.
- A role can be considered a "user", a "group", or both depending on how it is used.

```sql
CREATE ROLE developers WITH LOGIN CREATEDB CREATEROLE;
```

```sql
CREATE ROLE managers;

CREATE ROLE kenny WITH LOGIN password 'password' ;
CREATE ROLE lora WITH LOGIN password 'password' ;

GRANT kenny, lora TO managers;
```

## Remove role

```sql
REVOKE managers FROM lora;
```

## Grant permissions on the DB to the user

- `GRANT ALL ON DATABASE my_db TO kenny;` - grant all permissions
- `GRANT CONNECT ON DATABASE my_db TO kenny;` - grant connect
- `GRANT CREATE ON DATABASE my_db TO kenny;` - grant create DB objects
- `GRANT CONNECT CREATE ON DATABASE my_db TO kenny;` - grant connect, create
- `GRANT USAGE CREATE ON SCHEMA schema_name TO kenny;` - grant create on a schema
- `GRANT SELECT, INSERT, UPDATE ON TABLE my_table TO kenny;` - grant select, insert, update on a table

## Edit user

```sql
ALTER USER kenny INHERIT LOGIN;
```
