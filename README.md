# psql
```
\du
\l
```
## Docker
```
docker run --name postgres-db -e POSTGRES_PASSWORD=123456 -d postgres:alpine
docker exec -it -u postgres postgres-db psql
```
```
docker run --name postgres-db -e POSTGRES_PASSWORD=123456 -p 5432:5432 -d postgres:alpine
psql -U postgres -d postgres -h 127.0.0.1
```
## CREATE ROLE
```
CREATE ROLE name [ [ WITH ] option [ ... ] ]
```
where option can be:
```
      SUPERUSER | NOSUPERUSER
    | CREATEDB | NOCREATEDB
    | CREATEROLE | NOCREATEROLE
    | INHERIT | NOINHERIT
    | LOGIN | NOLOGIN
    | REPLICATION | NOREPLICATION
    | BYPASSRLS | NOBYPASSRLS
    | CONNECTION LIMIT connlimit
    | [ ENCRYPTED ] PASSWORD 'password' | PASSWORD NULL
    | VALID UNTIL 'timestamp'
    | IN ROLE role_name [, ...]
    | IN GROUP role_name [, ...]
    | ROLE role_name [, ...]
    | ADMIN role_name [, ...]
    | USER role_name [, ...]
    | SYSID uid
```
```
CREATE ROLE mohsen WITH SUPERUSER LOGIN;
CREATE ROLE test WITH LOGIN;
DROP ROLE rest;
```
