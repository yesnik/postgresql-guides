# Psql commands

## Log in

After PostgreSQL installation:

```bash
# Log in as postgres user
sudo su - postgres

# Run psql console
psql
```
See [create user](https://github.com/yesnik/postgresql-guides/blob/main/users.md#create-user)

## Console commands

- `psql -U kenny -h localhost -p 32770 -d sales` - connect to database `sales` as user `kenny`, host `localhost`, port `32770`
- `psql -U kenny -h localhost -d quiz_rails_development`
- `psql -U root -h localhost` - connect to database `root` as user `root`

## psql console commands

- `\l` / `\list` - show list of databases
- `\c sales` / `\connect sales` - use DB *sales*
- `\d` - show tables in active DB
- `\dS+ lots` - show columns in the `lots` table
- `\x` - toggle extended display of query results
- `\q` - quit console
