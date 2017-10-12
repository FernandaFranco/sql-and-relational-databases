# SQL

## Explain the difference between INNER, LEFT OUTER, and RIGHT OUTER joins.

JOINs are clauses in SQL statements to link two tables based on one or more fields. Uses the ON clause.

#### INNER

A inner join results in a table containing the common elements of the joined tables, i.e. the intersection where they match on the joined column.

#### LEFT OUTER

Takes all the rows from the left table, even if there are no matching rows in the right table. Results in all the matching rows from the left table along with any matching data from the RIGHT table based on the ON clause. If data is missing from the right table, fields will return NULL.

#### RIGHT OUTER

Similar to a LEFT JOIN

## Name and define the three sublanguages of SQL.

Different statements for different concerns.

#### DDL or Data Definition Language

Controls relation structure and rules. Create and modify schema. CREATE, DROP, ALTER, ADD

#### DML or Data Manipulation Language

Controls values stored within relations. Retrieve or modify data. SELECT, INSERT, UPDATE, DELETE

#### DCL or Data Control Language

Controls rights and access roles of users. GRANT

## Write SQL statements using INSERT, UPDATE, DELETE, CREATE/ALTER/DROP TABLE, ADD/ALTER/DROP COLUMN.

```sql CREATE TABLE contacts (id serial PRIMARY KEY, name text NOT NULL, phone varchar(10), email text);```

```INSERT INTO contacts (name, phone, email) VALUES ('Fernanda', '1231231234', 'fernanda@mail.com');```

```INSERT INTO contacts (name, phone, email) VALUES ('Eddie', '6171231234', 'eddie@mail.com');```

```INSERT INTO contacts (name, email) VALUES ('Seraphine', 'seraphine@mail.com');```

```UPDATE contacts SET email = 'fernanda@snail.com' WHERE name = 'Fernanda';```

```DELETE FROM ```

## Understand how to use GROUP BY, ORDER BY, WHERE, and HAVING.

# PostgreSQL

## Describe what a sequence is and what they are used for.

## Create an auto-incrementing column.

## Define a default value for a column.

## Be able to describe what primary, foreign, natural, and surrogate keys are.

## Create and remove CHECK constraints from a column.

## Create and remove foreign key constraints from a column.

# Database Diagrams

## Define cardinality and modality.

## Be able to draw database diagrams using crow's foot
notation.
