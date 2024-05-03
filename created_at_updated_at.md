# Created At and Updated At fields

1. Create function:
    ```sql
    CREATE OR REPLACE FUNCTION set_updated_at() 
    RETURNS TRIGGER 
    AS $$
    BEGIN 
      NEW.updated_at = NOW();
      RETURN NEW;
    END;
    $$ LANGUAGE plpgsql;
    ```
    Here we defined our function with a `RETURNS TRIGGER`. This opens up a special variable for us to use:
    `NEW` is a RECORD object. It contains the data that's being inserted or updated.
   As you can see in the example function, PostgreSQL allows us to read from and write to any field in the NEW object before it gets saved to disk.
2. Create table:
    ```sql
    CREATE TABLE users (
      id SERIAL PRIMARY KEY,
      username VARCHAR (50) UNIQUE NOT NULL,
      updated_at TIMESTAMP NOT NULL DEFAULT NOW(),
      created_at TIMESTAMP NOT NULL DEFAULT NOW()
    )
    ```
3. Create trigger:
    ```sql
    CREATE TRIGGER trigger_users_set_updated_at
    BEFORE UPDATE ON users
    FOR EACH ROW
    EXECUTE PROCEDURE set_updated_at();
    ```
    This trigger will execute the `trigger_users_set_updated_at` function that we defined earlier. It will do so whenever a row is updated in the `users` table.
4. Now both the `created_at` and `updated_at` columns will be saved correctly whenever we insert and update rows in the table.
