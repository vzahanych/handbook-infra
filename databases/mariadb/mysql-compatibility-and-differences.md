# MariaDB — MySQL compatibility and differences

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. What stays compatible](#1-what-stays-compatible)
  * [2. Where they diverge](#2-where-they-diverge)
  * [3. Migration considerations](#3-migration-considerations)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

MariaDB began as a drop-in MySQL replacement and still shares the wire protocol and most SQL, so clients and queries usually just work. Over the years, though, the two have diverged: version numbers no longer line up, JSON is implemented differently (MariaDB stores it as text with functions rather than a native binary type), and each has features the other lacks.

The practical consequence is that you cannot assume a MySQL feature, function, or behavior exists identically in MariaDB — verify anything non-trivial against your exact MariaDB version.

---

## Detailed explanation with examples

### 1. What stays compatible

- TODO: wire protocol, connectors, core SQL and types

### 2. Where they diverge

- TODO: version numbering; JSON; sequences; invisible columns
- TODO: replication and clustering (Galera vs Group Replication)

### 3. Migration considerations

- TODO: testing against the target version
- TODO: feature flags and reserved words

### 4. Practical rule

```text
Treat MariaDB as MySQL-compatible, but verify version-specific behavior.
Do not assume JSON/function parity across the two.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: pin features to the target engine + version; avoid assuming parity

### Operations and production

- TODO: test migrations on the exact MariaDB version; watch replication differences

## References

- Official docs: https://mariadb.com/kb/en/mariadb-vs-mysql-compatibility/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [../mysql/fundamentals.md](../mysql/fundamentals.md)
