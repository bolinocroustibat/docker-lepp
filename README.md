# LEMP ((Linux) + (E)nginx + MariaDB + PHP) Docker stack for local web development

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
- Export env variable `MYSQL_ROOT_PASSWORD` for defining your MySQL root password:
```sh
export MYSQL_ROOT_PASSWORD="root"
```
*WARNING! The root password variable will only be used when creating a database, it won't change the root password of an existing database. And databases are persistent in a volume, even if the image is destroyed and recreated.*

- Start Docker compose:
```ssh
docker-compose up -d
```

- Access the website at document root on the URL `http://localhost:8080/` or `http://127.0.0.1:8080/` (both work).


## Note on how to connect to MariaDB database from PHP container

Ports are ignored for connections between containers, so use 3306 (default), and the host name is the mariadb container name. So, i.e.:

```php
try {
    $db = new PDO('mysql:host=mariadb;dbname=my_db_name', 'root', 'root');
}
catch(Exception $e) {
    die('Error: '.$e->getMessage());
}
```

## 

