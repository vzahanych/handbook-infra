# TimescaleDB — compression and retention

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Chunk compression](#1-chunk-compression)
  * [2. Retention policies](#2-retention-policies)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Time-series data is written once and rarely changed, which lets TimescaleDB compress older chunks into a columnar format that shrinks storage dramatically and speeds up large scans. You enable compression and a policy automatically compresses chunks past a certain age, while a separate retention policy drops chunks older than a chosen window — cheap because it deletes whole chunks rather than individual rows.

Together these turn the natural lifecycle of time-series data into automatic operations: recent data stays hot and writable, middle-aged data gets compressed, and ancient data is dropped. Setting both policies is what keeps storage flat and predictable over time.

---

## Detailed explanation with examples

### 1. Chunk compression

- TODO: columnar compression of old chunks; `add_compression_policy`
- TODO: segment-by / order-by compression settings

### 2. Retention policies

- TODO: `add_retention_policy`; dropping whole chunks
- TODO: interaction with continuous aggregates

### 3. Practical rule

```text
Compress aging chunks; drop chunks past your retention window.
Both operate on whole chunks, so they stay cheap.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: treat compressed chunks as mostly read-only

### Operations and production

- TODO: set compression + retention policies; monitor compression ratio and disk

## References

- Official docs: https://docs.tigerdata.com/
- Overview: [fundamentals.md](fundamentals.md)
