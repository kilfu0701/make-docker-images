## Build image and upload to docker hub
```sh
docker build -t <YOURNAME>/py3-postgres .
docker push <YOURNAME>/py3-postgres
```

## Run image after built
```sh
docker run -it <YOURNAME>/py3-postgres /bin/bash
```

## Use docker hub image with docker-compose

- docker-compose.yml
```yaml
version: '3'

services:
  local-dev:
    image: <YOURNAME>/py3-postgres
    container_name: local-dev
    volumes:
      - ./volumes/postgres/data:/var/lib/postgresql/data:rw
    environment:
      TZ: JST-9
      POSTGRES_INITDB_ARGS: '--encoding=UTF-8 --lc-collate=ja_JP.UTF-8 --lc-ctype=ja_JP.UTF-8 --lc-messages=ja_JP.UTF-8'
      POSTGRES_DB: service_development
    sysctls:
      net.core.somaxconn: 8192
    expose:
      - "5432"
    ports:
      - "5432:5432"
    restart: "no"
```

- run compose
```sh
docker-compose up --build

docker-compose exec local-dev /bin/bash

## get into postgres 
$ psql -U postgres -w

## show databases
postgres=# \l
                                      List of databases
        Name         |  Owner   | Encoding |   Collate   |    Ctype    |   Access privileges
---------------------+----------+----------+-------------+-------------+-----------------------
 service_development | postgres | UTF8     | ja_JP.UTF-8 | ja_JP.UTF-8 |
 postgres            | postgres | UTF8     | ja_JP.UTF-8 | ja_JP.UTF-8 |
 template0           | postgres | UTF8     | ja_JP.UTF-8 | ja_JP.UTF-8 | =c/postgres          +
                     |          |          |             |             | postgres=CTc/postgres
 template1           | postgres | UTF8     | ja_JP.UTF-8 | ja_JP.UTF-8 | =c/postgres          +
                     |          |          |             |             | postgres=CTc/postgres
(4 rows)

## Let's create a tests database
postgres=# create database tests;
CREATE DATABASE
```
