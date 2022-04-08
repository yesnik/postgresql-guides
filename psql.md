# Psql commands

- `psql -h localhost -p 32770 -U kenny -d sales` - connect to database `sales` as user `kenny`, host `localhost`, port `32770`
- `psql -h localhost -U kenny -d quiz_rails_development`

## psql console commands

- `\l` / `\list` - show list of databases
- `\c sales` / `\connect sales` - use DB *sales*
- `\d` - show tables in active DB
- `\dS+ lots` - show columns in the `lots` table
- `\x` - toggle extended display of query results
- `\q` - quit console
