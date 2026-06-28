# SQLite — one file and no server

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. A library, not a server](#1-a-library-not-a-server)
  * [2. Attaching databases and special schemas](#2-attaching-databases-and-special-schemas)
  * [3. Journal modes](#3-journal-modes)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

SQLite is not a server you connect to; it is a library that reads and writes an ordinary file, and that file holds the entire database — schema, tables, indexes, and data. Your application links the library and opens the file directly, which is why SQLite is the default choice for embedded systems, desktop and mobile apps, and test suites.

You can attach more than one database file to a connection, and there are special schemas like `main` and `temp`. The journal mode — rollback or write-ahead logging — decides how durability and concurrency work against that single file.

---

## Detailed explanation with examples

### 1. A library, not a server

- TODO: in-process; one file = one database
- TODO: zero-configuration; no network layer

### 2. Attaching databases and special schemas

- TODO: `ATTACH DATABASE`; `main`, `temp`
- TODO: cross-database queries

### 3. Journal modes

- TODO: rollback journal vs WAL
- TODO: durability vs concurrency trade-offs

### 4. Practical rule

```text
Great for embedded/local/test use; keep the file on local disk.
Enable WAL for concurrent readers.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: one file per logical database; attach only when needed

### Operations and production

- TODO: avoid network filesystems; use WAL; back up with the backup API/`VACUUM INTO`

## References

- Official docs: https://www.sqlite.org/docs.html
- Overview: [fundamentals.md](fundamentals.md)
