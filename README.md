# LEMP (Nginx + MariaDB + PHP) Docker stack for local web development

A docker-compose stack for local web development, which includes:
- Nginx 1.20
- MariaDB 10.5
- PHP 7.4

There is also a LAMP (Apache + MariaDB + PHP) Docker stack available [on this branch](https://github.com/bolinocroustibat/docker-lemp/tree/lamp).


## How to run

- Install Docker

- Export env variable `WWW_DOCUMENT_ROOT` to point to your project root directory:
```sh
export WWW_DOCUMENT_ROOT="/var/www/html"
```
- Start Docker compose:
```ssh
docker-compose up -d
```

- Access the website at document root on the URL `http://localhost:8080/` or `http://127.0.0.1:8080/` (both work).
