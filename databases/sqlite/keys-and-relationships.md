# SQLite — keys and relationships

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Primary keys and rowid](#1-primary-keys-and-rowid)
  * [2. Foreign keys are off by default](#2-foreign-keys-are-off-by-default)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Keys in SQLite work as in other relational databases, with one important default to remember: foreign key enforcement is off unless you turn it on per connection with `PRAGMA foreign_keys = ON`. The primary key usually maps to the built-in `rowid`, and declaring a column `INTEGER PRIMARY KEY` makes it the rowid alias and the most efficient key.

Other primary keys and unique constraints are backed by indexes. Because foreign keys are silent by default, relationships you assume are enforced may not be.

---

## Detailed explanation with examples

### 1. Primary keys and rowid

- TODO: `INTEGER PRIMARY KEY` aliases rowid
- TODO: composite and non-integer primary keys

### 2. Foreign keys are off by default

- TODO: `PRAGMA foreign_keys = ON` per connection
- TODO: referential actions when enabled

### 3. Practical rule

```text
Turn on foreign keys on every connection.
Use INTEGER PRIMARY KEY for the efficient rowid alias.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: enable `foreign_keys` in connection setup code, every time

### Operations and production

- TODO: verify FK pragma is set in ORMs/drivers (many don't by default)

## References

- Official docs: https://www.sqlite.org/foreignkeys.html
- Overview: [fundamentals.md](fundamentals.md)
