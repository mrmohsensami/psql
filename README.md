# psql - RDBMS - Relational Database Management System
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
 CREATE ROLE sami WITH SUPERUSER LOGIN password '123';
CREATE ROLE test WITH LOGIN;
DROP ROLE rest;
```
## create database
```
CREATE DATABASE mydb;
CREATE DATABASE mydb WITH OWNER = mohsen;
\l
\conninfo
DROP DATABASE mydb;
```
## Tables
```
CREATE TABLE name (
      -- col_name col_datatype *col_options
      id INTEGER PRIMARY KEY,
      name VARCHAR(32)
);
```
```
\d
\d names
```
exaple phone_book
```
CREATES DATABASE phone_book;
\c phone_book;
CREATE TABLE phone_book (
      id SERIAL PRIMARY KEY,
      first_name VARCHAR(32) NOT NULL,
      last_name VARCHAR(32) NOT NULL,
      phone_number CHAR(12) NOT NULL UNIQUE 
);
\d
\d phone_book
```
## INSERT
```
INSERT INTO phone_book VALUES (1, 'mohsen', 'sami', '989033451850');
INSERT INTO phone_book (first_name, last_name, phone_number) VALUES ('mohsen', 'sami', '989033451850');
SELECT * FROM phone_book;
DELETE FROM phone_book;
```
## READING
```
SELECT * FROM phone_book;
SELECT first_name AS "First Name", last_name, phone_number FROM phone_book;
SELECT CONCAT(first_name, ' ', last_name) AS "Full Name" FROM phone_book;
```
```
SELECT * FROM phone_book WHERE LOWER(first_name) = 'mohsen';
EXPLAIN ANALYZE SELECT * FROM phone_book WHERE LOWER(first_name) = 'mohsen';
SELECT * FROM phone_book WHERE ID < 5 ORDER BY last_name ASC;
SELECT * FROM phone_book LIMIT 10;
SELECT * FROM phone_book OFFSET 10;
```
## Update
```
UPDATE phone_book SET first_name=name WHERE id=2;
```
