# Data Types

See [docs](https://www.postgresql.org/docs/current/datatype.html)

## Numeric Types

### Integer

- `smallint` (`int2`) - signed 2 byte integer
- `integer` (`int`, `int4`) - signed 4 byte integer
- `bigint` (`int8`) - signed 8 byte integer
- `serial` (`serial4`) - autoincrementing 4 byte integer
- `bigserial` (`serial8`) - autoincrementing 8 byte integer

### Float

- `real` (`float4`) - single precision floating-point number (4 bytes)
- `double precision` (`float`, `float8`) - double precision floating-point number (8 bytes)
- `numeric(10, 2)` (`decimal(10, 2)`) - exact numeric of selectable precision

## Monetary

- `money` - currency amount. For `en_US` language 12345,6 will be `$1,234.56`

## Character Types

- `character(n)` (char(n)) - fixed-length character string
- `character varying(n)` (`varchar(n)`) - variable-length character string
- `text` - variable-length character string

The only difference between `TEXT` and `VARCHAR(n)` is that you can limit the maximum length of a `VARCHAR` column, 
for example, VARCHAR(255) does not allow inserting a string more than `255` characters long.
Both `TEXT` and `VARCHAR` have the *upper limit at 1 Gb*, and there is no performance difference among them.

## Date / Time Types

- `date` - calendar date `YYYY-MM-DD`
- `time` - time `HH:MM:SS`
- `TIMESTAMP` - date and time `YYYY-MM-DD HH:MM:SS`
- `TIMESTAMP WITH TIME ZONE` - date and time with timezone `YYYY-MM-DD HH:MM:SS +hh:mi`

## UUID Type

`uuid` - stores Universally Unique Identifiers (UUID). This identifier is a 128-bit quantity. Example: `a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a12`

## Network Address Types

- `inet` - IPv4 or IPv6 host address. Example: `192.168.1.1`, `192.168.1.0/24`

## Arrays Types

- `names TEXT[]` - array of strings. Example: `UPDATE public.products SET names = '{apple, orange}' WHERE id = 1;`
- `stars INT[]` - array of int. Example: `UPDATE public.products p SET stars = array[3, 4, 5, 5] WHERE id = 1`

## Composite Types

```sql
CREATE TYPE point AS (
    x INT,
    y INT
);

CREATE TABLE stores (
    id SERIAL PRIMARY KEY,
    position point
);

INSERT INTO stores (position) VALUES (point(1, 2));
```

## XML Type

`xml` - type can be used to store XML data. Its advantage over storing XML data in a `text` field is that it checks the input values for well-formedness.

Example: `UPDATE products SET xml_feed = '<root><id at="2" no="2">5</id><name>Ken</name></root>' WHERE id = 1;`

## JSON Types

JSON data types are for storing JSON (JavaScript Object Notation) data.

- `json` - stores an exact copy of the input text, which processing functions must reparse on each execution
- `jsonb` - data is stored in a decomposed binary format that makes it slightly slower to input due to added conversion overhead, 
  but significantly faster to process, since no reparsing is needed. `jsonb` also supports indexing, which can be a significant advantage.

```sql
update products SET jsonb_params = '{"name": "Lora", "age": 23}' where id = 4;
select jsonb_params->>'name' from products;
```
