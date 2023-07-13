# LEPP ((Linux) + (E)nginx  + PostgreSQL + PHP) Docker stack for local web development

A docker-compose stack for local web development, which includes:
- Nginx 1.22.1
- PostgreSQL 15.1
- PHP 8.0

There is also a LEMP (Nginx + MariaDB + PHP) Docker stack available [on this repo](https://github.com/bolinocroustibat/docker-lemp).

...and a LAMP (Apache + MariaDB + PHP) Docker stack available [on this repo](https://github.com/bolinocroustibat/docker-lamp).

## How to run

- Install Docker

- Export env variable `WWW_DOCUMENT_ROOT` to point to your project root directory:
```sh
export WWW_DOCUMENT_ROOT="/var/www/html"
```

- Export env variable `POSTGRES_DB` for defining your default PostgreSQL database:
```sh
export POSTGRES_DB="postgres"
```

- Start Docker compose:
```ssh
docker-compose up -d
```

- Access the website at document root on the URL `http://localhost:8080/` or `http://127.0.0.1:8080/` (both work).

## How to migrate a local MySQL DB to PostgreSQL DB

```sh
pgloader mysql://root:root@localhost:8889/db-name postgresql://postgres:postgres@localhost:5432/db-namee
```

You can then migrate the schema to public:
```sql
DO
$$
DECLARE
    row record;
BEGIN
    FOR row IN SELECT tablename FROM pg_tables WHERE schemaname = 'db_name' -- and other conditions, if needed
    LOOP
        EXECUTE 'ALTER TABLE "db_name".' || quote_ident(row.tablename) || ' SET SCHEMA public;';
    END LOOP;
END;
$$;

DROP SCHEMA "db_name";
```
