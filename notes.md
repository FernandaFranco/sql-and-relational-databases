# operators

evaluates conditions in sql queries.

## comparison

=
<
>
<=
>=

## logical

almost exclusively used in the WHERE clause of queries.

## LIKE

# functions

## string
TRIM, LTRIM, RTRIM

## aggregate

SUM() returns the sum of all values in a column

## date/time

## mathematical

# data analysis with GROUP BY

# Normal form

PROS:

Allows more complex realtionships (many to many)

CONS:

Can take multiple joins to retrieve, which makes it inefficient

May be designed expecting a pattern but that pattern only has a few occurencies (may be denormalized)

# Data formats

INTERVAL

# Indexes

Best used in tables where reads are more common

# pg_dump and pg_restore

# WHAT KIND OF PROGRAMMING LANGUAGE IS SQL?

a special purpose language since it's basically only used to interact with relational databases.

# DDL, DML, DCL

# Keys

Natural keys (name, phone number, ssn) vs Surrogate key (id)

PRIMARY KEYS vs NOT NULL UNIQUE

# ORDER BY

ASC ascending vs DESC descending order

# How PostgreSQL executes queries

query and database optimization

SELECT queries can be very complex

#DML
Manipulation: CREATE, READ, UPDATE, DELETE THE ACTUAL DATA.

SELECT
INSERT
UPDATE
DELETE

#DDL
Definition: Create, modify and delete databases and tables. Describing how data is structured.

CREATE TABLE
ALTER
DROP

---
SELECT column_name FROM my_table;

The above is a DML statement, since it manipulates the data and not the structure of the table/database.

---
CREATE TABLE things (
  id serial PRIMARY KEY,
  item text NOT NULL UNIQUE,
  material text NOT NULL
);

On the other hand, the above statement is a DDL component, because it defines the type of information stored in a db table.

---
ALTER TABLE things
DROP CONSTRAINT thing_item_key;

This is a DDL statement.

---
INSERT INTO things VALUES (3, 'Scissors', 'Metal');

This is a DML component since it adds more data to the table.

---
UPDATE things
SET material = 'plastic'
WHERE item = 'Cup';

UPDATE is DML since it changes the data;

---
\d

\d is a psql console (meta) command, but it does act like a DDL statement since it displays the schema of the db/table;

---
DELETE FROM things WHERE item = 'Cup';

DML

---
DROP DATABASE xyzzy;

DDL and DML because it deletes the whole structure, including all the data.

---
CREATE SEQUENCE part_number_sequence;










