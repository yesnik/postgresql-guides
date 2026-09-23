# Data Types

See [docs](https://www.postgresql.org/docs/current/datatype.html)

Integer:

- `smallint` (`int2`) - signed 2 byte integer
- `integer` (`int`, `int4`) - signed 4 byte integer
- `bigint` (`int8`) - signed 8 byte integer
- `numeric(10, 2)` (`decimal(10, 2)`) - exact numeric of selectable precision

Float:

- `real` (`float4`) - single precision floating-point number (4 bytes)
- `double precision` (`float`, `float8`) - double precision floating-point number (8 bytes)
- `money` - currency amount. For `en_US` language 12345,6 will be `$1,234.56`

Serial:

- `serial` (`serial4`) - autoincrementing 4 byte integer
- `bigserial` (`serial8`) - autoincrementing 8 byte integer

Character Types:

- `character(n)` (char(n)) - fixed-length character string
- `character varying(n)` (`varchar(n)`) - variable-length character string
- `text` - variable-length character string

The only difference between `TEXT` and `VARCHAR(n)` is that you can limit the maximum length of a `VARCHAR` column, 
for example, VARCHAR(255) does not allow inserting a string more than `255` characters long.
Both `TEXT` and `VARCHAR` have the *upper limit at 1 Gb*, and there is no performance difference among them.

Date and time

- `date` - calendar date `YYYY-MM-DD`
- `time` - time `HH:MM:SS`
- `TIMESTAMP` - date and time `YYYY-MM-DD HH:MM:SS`
- `TIMESTAMP WITH TIME ZONE` - date and time with timezone `YYYY-MM-DD HH:MM:SS +hh:mi`

- `uuid` - stores Universally Unique Identifiers (UUID). This identifier is a 128-bit quantity. Example: `a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a12`
- `inet` - IPv4 or IPv6 host address. Example: `192.168.1.1`, `192.168.1.0/24`
- 
