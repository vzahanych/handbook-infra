# PostgreSQL — cluster, database, and schema

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The four nesting levels](#1-the-four-nesting-levels)
  * [2. Schemas and search_path](#2-schemas-and-search_path)
  * [3. System catalogs](#3-system-catalogs)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

PostgreSQL nests data in levels: a running server, called a cluster, holds many databases; each database holds schemas; and each schema holds tables and other objects. A client connection picks one database and stays there, so you cannot join across databases the way you can across schemas.

Schemas are the namespace you organize with day to day, and the `search_path` decides which ones are consulted when you write an unqualified table name. The `public` schema exists by default, which is convenient but worth locking down in shared databases.

---

## Detailed explanation with examples

### 1. The four nesting levels

- TODO: cluster (server + data directory) → database → schema → table
- TODO: connections are scoped to one database
- TODO: when to use multiple databases vs multiple schemas

### 2. Schemas and search_path

- TODO: `CREATE SCHEMA`; qualified vs unqualified names
- TODO: `search_path` resolution order
- TODO: locking down `public`

### 3. System catalogs

- TODO: `pg_catalog` and `information_schema`
- TODO: inspecting objects with `\d`, catalog queries

### 4. Practical rule

```text
Use schemas to organize one database; reach for separate databases only for hard isolation.
Set an explicit search_path; do not rely on a permissive public schema.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: namespace by schema per module/tenant where it helps
- TODO: always schema-qualify in migrations and shared code

### Operations and production

- TODO: revoke default `public` schema create rights on shared DBs
- TODO: manage roles/grants per schema

## References

- Official docs: https://www.postgresql.org/docs/
- Overview: [fundamentals.md](fundamentals.md)
