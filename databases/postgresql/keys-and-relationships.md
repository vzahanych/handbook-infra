# PostgreSQL — keys and relationships

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Primary keys](#1-primary-keys)
  * [2. Unique constraints](#2-unique-constraints)
  * [3. Foreign keys](#3-foreign-keys)
  * [4. Surrogate versus natural keys](#4-surrogate-versus-natural-keys)
  * [5. Practical rule](#5-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Keys are how PostgreSQL enforces identity and links tables together. A primary key uniquely identifies each row and is usually a surrogate integer or UUID, while additional unique constraints guard other natural identifiers such as an email address.

Foreign keys connect a row to its parent in another table and let the database enforce referential actions like cascading deletes, so orphaned rows never appear. Modeling these relationships in the schema, rather than only in application code, is what keeps a relational database consistent.

---

## Detailed explanation with examples

### 1. Primary keys

- TODO: `PRIMARY KEY`; one per table
- TODO: integer/identity vs UUID trade-offs

### 2. Unique constraints

- TODO: `UNIQUE`; multi-column uniqueness
- TODO: relationship to indexes (a unique constraint creates one)

### 3. Foreign keys

- TODO: `REFERENCES`, `ON DELETE`/`ON UPDATE` actions
- TODO: index the referencing column

### 4. Surrogate versus natural keys

- TODO: when a natural key is appropriate
- TODO: trade-offs of surrogate keys

### 5. Practical rule

```text
Give every table a primary key; index foreign key columns.
Use surrogate keys by default; add unique constraints for natural identifiers.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: declare foreign keys; do not enforce relationships only in code
- TODO: add an index on each FK column to avoid slow cascades/joins

### Operations and production

- TODO: be aware FK checks add write cost; validate large FK additions carefully

## References

- Official docs: https://www.postgresql.org/docs/
- Overview: [fundamentals.md](fundamentals.md)
