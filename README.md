# LEPP ((Linux) + (E)nginx  + PostgreSQL + PHP) Docker stack for local web development

A docker-compose stack for local web development, which includes:
- Nginx 1.20
- PostgreSQL 14.2
- PHP 7.4

There is also a LEMP (Nginx + MariaDB + PHP) Docker stack available [on this branch](https://github.com/bolinocroustibat/docker-lemp/tree/main).
...and a LAMP (Apache + MariaDB + PHP) Docker stack available [on this branch](https://github.com/bolinocroustibat/docker-lemp/tree/lamp).

## How to run

- Install Docker

- Export env variable `POSTGRES_DB` for defining your PostgreSQL database:
```sh
export POSTGRES_DB="postgres"
```

- Start Docker compose:
```ssh
docker-compose up -d
```

- Access the website at document root on the URL `http://localhost:8080/` or `http://127.0.0.1:8080/` (both work).

