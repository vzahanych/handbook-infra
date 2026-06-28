# ClickHouse — columnar storage

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Columns stored separately](#1-columns-stored-separately)
  * [2. Why OLAP, not OLTP](#2-why-olap-not-oltp)
  * [3. Compression](#3-compression)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

ClickHouse stores each column of a table in its own files rather than storing whole rows together, and this single choice explains most of its behavior. Analytical queries usually read a few columns across many rows, so reading only the needed columns — already sorted and heavily compressed — is dramatically faster than scanning entire rows.

The trade-off is that fetching or modifying a single complete row is comparatively expensive, which is why ClickHouse is an OLAP system for aggregation, not an OLTP system for record-by-record updates. You feed it large batched inserts and ask it wide analytical questions.

---

## Detailed explanation with examples

### 1. Columns stored separately

- TODO: per-column files; reading only needed columns

### 2. Why OLAP, not OLTP

- TODO: batch inserts, few updates; point lookups are costly

### 3. Compression

- TODO: per-column compression; codecs (`LZ4`, `ZSTD`, `Delta`)

### 4. Practical rule

```text
Read few columns over many rows; insert in big batches.
Don't use ClickHouse for row-by-row OLTP.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: select only needed columns; use `LowCardinality` for repetitive strings

### Operations and production

- TODO: choose compression codecs per column; avoid tiny inserts

## References

- Official docs: https://clickhouse.com/docs
- Overview: [fundamentals.md](fundamentals.md)
