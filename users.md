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

## Grant all permissions to DB

```sql
GRANT ALL ON DATABASE my_db TO kenny;
```

## Edit user

```sql
ALTER USER kenny INHERIT LOGIN;
```
