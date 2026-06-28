# ScyllaDB — differences from Cassandra

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. No JVM, no garbage collector](#1-no-jvm-no-garbage-collector)
  * [2. Self-tuning schedulers](#2-self-tuning-schedulers)
  * [3. Feature and tooling differences](#3-feature-and-tooling-differences)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Although ScyllaDB is a drop-in for Cassandra at the CQL level, the implementation differs in ways that matter operationally. There is no JVM and no garbage collector, so latency is more predictable and there is no GC tuning, and Scylla self-tunes its own internal schedulers for compaction, repair, and queries rather than relying on hand-set thread pools.

Some features, defaults, and tooling differ between the two, and shard-aware drivers are needed to get the full performance benefit. Treat it as Cassandra-compatible for modeling but verify operational specifics against Scylla's own documentation.

---

## Detailed explanation with examples

### 1. No JVM, no garbage collector

- TODO: C++ engine; predictable latency; no GC tuning

### 2. Self-tuning schedulers

- TODO: internal schedulers for compaction/repair/queries

### 3. Feature and tooling differences

- TODO: differing defaults/features; Scylla Manager/Monitoring
- TODO: shard-aware drivers

### 4. Practical rule

```text
Model like Cassandra; verify ops specifics (defaults, tooling) in Scylla docs.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: don't assume identical defaults/feature flags to Cassandra

### Operations and production

- TODO: use Scylla Manager/Monitoring; let the DB self-tune rather than hand-tuning JVM-style

## References

- Official docs: https://docs.scylladb.com/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [../cassandra/fundamentals.md](../cassandra/fundamentals.md)
