# Kafka — topics and partitions

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Topics as named logs](#1-topics-as-named-logs)
  * [2. Partitions and ordering](#2-partitions-and-ordering)
  * [3. Choosing a partition count](#3-choosing-a-partition-count)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

A Kafka topic is a named, append-only log, and it is physically divided into partitions, each an independent ordered sequence of records. Ordering is guaranteed only within a partition, never across them, so the partition is both the unit of ordering and the unit of parallelism — more partitions allow more consumers to read in parallel.

Each partition is stored and replicated independently across brokers, which is how a single topic spreads its load and its durability across the cluster. The partition count is a sizing decision that is easy to increase but awkward to decrease, so it is worth choosing with target throughput in mind.

---

## Detailed explanation with examples

### 1. Topics as named logs

- TODO: append-only log; records are not deleted on read
- TODO: many consumers read the same topic independently

### 2. Partitions and ordering

- TODO: ordering within a partition only
- TODO: partitions distributed/replicated across brokers

### 3. Choosing a partition count

- TODO: partitions = max parallelism; increasing vs decreasing
- TODO: per-partition throughput and overhead

### 4. Practical rule

```text
Ordering is per partition — never assume global order.
Size partitions for peak consumer parallelism; you can add but not easily remove.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: rely on per-partition ordering only; design around it

### Operations and production

- TODO: avoid extreme partition counts (overhead); plan growth ahead

## References

- Official docs: https://kafka.apache.org/documentation/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [producers-and-keys.md](producers-and-keys.md)
