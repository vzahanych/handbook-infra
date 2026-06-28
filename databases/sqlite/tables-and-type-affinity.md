# SQLite — tables and type affinity

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Type affinity](#1-type-affinity)
  * [2. Rowid and WITHOUT ROWID tables](#2-rowid-and-without-rowid-tables)
  * [3. STRICT tables](#3-strict-tables)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

SQLite stores tables of rows and columns like any SQL database, but its typing is unusual: instead of strict column types it uses type affinity, where a column declaration is a preference for how values are stored, not a hard rule. A column declared INTEGER will happily store text unless you opt into a STRICT table, which enforces declared types.

Every ordinary table also has a hidden 64-bit `rowid` that identifies rows, and declaring `INTEGER PRIMARY KEY` simply aliases it. Knowing affinity exists prevents surprise when a value comes back in a type you did not expect.

---

## Detailed explanation with examples

### 1. Type affinity

- TODO: affinities (TEXT, NUMERIC, INTEGER, REAL, BLOB)
- TODO: how a declared type maps to an affinity

### 2. Rowid and WITHOUT ROWID tables

- TODO: the implicit `rowid`
- TODO: `WITHOUT ROWID` tables and when to use them

### 3. STRICT tables

- TODO: `STRICT` to enforce declared types
- TODO: allowed types in strict mode

### 4. Practical rule

```text
Use STRICT tables when you want real type enforcement.
Declare INTEGER PRIMARY KEY to alias the efficient rowid.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: prefer STRICT tables in new schemas; validate at the app boundary otherwise

### Operations and production

- TODO: be aware older SQLite versions lack STRICT; check the bundled version

## References

- Official docs: https://www.sqlite.org/docs.html
- Overview: [fundamentals.md](fundamentals.md)
- Related: [indexes.md](indexes.md)
