# SQL

## Explain the difference between INNER, LEFT OUTER, and RIGHT OUTER joins.

JOINs are clauses in SQL statements to link two tables based on one or more fields. Uses the ON clause.

#### INNER

A inner join results in a table containing only the rows from both tables that match. This returns the common elements of the joined tables, i.e. the intersection where they match on the joined column.

#### LEFT OUTER

Takes all the rows from the left table, even if there are no matching rows in the right table. Results in all the matching rows from the left table along with any matching data from the RIGHT table based on the ON clause. If data is missing from the right table, fields will return NULL.

#### RIGHT OUTER

Similar to a LEFT JOIN

## Name and define the three sublanguages of SQL.

Different statements for different applications.

#### DDL or Data Definition Language

Controls relation structure and rules. Create and modify schema. CREATE, DROP, ALTER, ADD

#### DML or Data Manipulation Language

Controls values stored within relations. Retrieve or modify data. SELECT, INSERT, UPDATE, DELETE

#### DCL or Data Control Language

Controls rights and access roles of users. GRANT

## Write SQL statements using INSERT, UPDATE, DELETE, CREATE/ALTER/DROP TABLE, ADD/ALTER/DROP COLUMN.

```SQL
CREATE TABLE contacts (id serial PRIMARY KEY, name text NOT NULL, phone text, email text);

INSERT INTO contacts (name, phone, email) VALUES ('Fernanda', '1231231234', 'fernanda@mail.com');

INSERT INTO contacts (name, phone, email) VALUES ('Eddie', '6171231234', 'eddie@mail.com');

INSERT INTO contacts (name, email) VALUES ('Seraphine', 'seraphine@mail.com');

CREATE TYPE category_type AS ENUM ('family', 'friends', 'work');

ALTER TABLE contacts ADD COLUMN category category_type;

UPDATE contacts SET category = 'family' WHERE name = 'Fernanda';

UPDATE contacts SET category = 'work' WHERE name = 'Eddie';

ALTER TABLE contacts ALTER COLUMN phone TYPE varchar(20);

DELETE FROM contacts WHERE phone IS NULL;

ALTER TABLE contacts DROP COLUMN email;

DROP TABLE contacts;
```

## Understand how to use `GROUP BY`, `ORDER BY`, `WHERE`, and `HAVING`.

#### GROUP BY

`GROUP BY` is a clause which can be used in the select statement to group rows by a specified field. It requires an aggregation function.  Both GROUP BY and aggregate functions perform grouping.

```SQL
SELECT count(id), category FROM contacts GROUP BY category;
```

#### ORDER BY

`ORDER BY` sorts the results by a field and order specified in the clause.

```SQL
SELECT name, phone FROM contacts ORDER BY name ASC;
```

#### WHERE

`WHERE` is a clause added to a SQL statement to filter the returned data with a condition. Only the records with the field value equal to the value in our condition will be returned.

```SQL
SELECT * FROM contacts WHERE name = 'Fernanda';
```

#### HAVING

Similarly to the `WHERE` clause, `HAVING` conditions are used to filter rows, but `HAVING` is applied to the values used to create groups instead of individual rows.

```SQL
SELECT count(id), category FROM contacts GROUP BY category HAVING count(id) > 1;
```

# PostgreSQL

## Describe what a sequence is and what they are used for.

A sequence is a relation that generates a sequential series of numbers. It will remember the last number it generated, so every time we pass it to the function `nextval` it will return the next number not returned before.

## Create an auto-incrementing column.

```SQL
CREATE SEQUENCE sequence;

SELECT nextval('sequence');
SELECT nextval('sequence');
```

```SQL
CREATE SEQUENCE even_counter INCREMENT BY 2 MINVALUE 0;

SELECT nextval('even_counter');
SELECT nextval('even_counter');
DROP SEQUENCE even_counter;
```
Besides that, using `serial` as the column type is just a short-hand in PostgreSQL for this:

 ```SQL
CREATE SEQUENCE contacts_id_seq;
CREATE TABLE contacts (
  id integer NOT NULL DEFAULT nextval('contacts_id_seq'),
  name text
);
 ```
## Define a default value for a column.

```SQL
ALTER TABLE contacts ALTER COLUMN category SET DEFAULT 'friends';
```

## Be able to describe what primary, foreign, natural, and surrogate keys are.

#### Primary Key

Creates an index on a column that makes sure the column will only hold unique not null values. Only one primary key per table is allowed. It's a convention to have a primary key in every table called `id`.

#### Foreign Key

Creates an constraint on a column that makes it reference another table's primary key.

To create a foreign key column, simply create a column of the same type as the primary key column it will point to.

To create a foreign key constraint,

#### Natural Key

A existing value that can be used to uniquely identify each row: Social Security number, car plate etc; The problem is that natural keys can stop being unique over time. A solution would be using more than one natural key together forming a composite key.

#### Surrogate Key

Created solely for the purpose of identifying a row in a table. The most common example is an auto-incrementing integer in order to remain unique for every row.

## Create and remove CHECK constraints from a column.

```SQL
ALTER TABLE contacts ADD CHECK (length(name) >= 3 AND position(' ' in name) > 0);

ALTER TABLE contacts DROP CONSTRAINT contacts_name_check;
```

## Create and remove foreign key constraints from a column.

```SQL
CREATE TABLE calls_placed (
  id serial PRIMARY KEY,
  date timestamp DEFAULT NOW(),
  contact_id integer NOT NULL REFERENCES contacts(id)
);
```

# Database Diagrams

## Define cardinality and modality.

#### Cardinality

The number of objects on each side of the relationship. Options for each side are one (In crow's foot notation, a simple straight line) or many (a crow's foot shape).

Types of relationships are:

One-to-one 1:1
One-to-many 1:M
Many-to-many M:M

#### Modality

Indicates if the relationship is required (1 or more) or not (0 or more). In crow's foot notation those are represented by a circle (optional) or a perpendicular line (required).

## Be able to draw database diagrams using crow's foot
notation.

