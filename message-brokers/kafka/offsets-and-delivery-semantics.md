# Kafka — offsets and delivery semantics

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Offsets and commits](#1-offsets-and-commits)
  * [2. The three delivery guarantees](#2-the-three-delivery-guarantees)
  * [3. Exactly-once processing](#3-exactly-once-processing)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

An offset is a consumer's position in a partition, and committing an offset records how far it has read. The timing of that commit relative to processing is what determines the delivery guarantee: commit before processing and a crash loses messages (at-most-once); commit after processing and a crash reprocesses them (at-least-once).

At-least-once is the common default, which is why consumers should be idempotent so reprocessing is harmless. Exactly-once is achievable for Kafka-to-Kafka workloads using idempotent producers and transactions, but it is narrower and costlier than it sounds, so most systems choose at-least-once plus idempotency.

---

## Detailed explanation with examples

### 1. Offsets and commits

- TODO: auto vs manual commit; commit timing
- TODO: offsets stored in `__consumer_offsets`

### 2. The three delivery guarantees

- TODO: at-most-once, at-least-once, exactly-once
- TODO: where each comes from (commit ordering)

### 3. Exactly-once processing

- TODO: idempotent producer + transactions; `read_committed`
- TODO: scope/limits of EOS

### 4. Practical rule

```text
Default to at-least-once + idempotent consumers.
Commit offsets only after processing succeeds.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: manual-commit after success; make handlers idempotent
- TODO: use transactions only for true Kafka-to-Kafka exactly-once

### Operations and production

- TODO: alert on lag growth; verify commit strategy under failure tests

## References

- Official docs: https://kafka.apache.org/documentation/
- Overview: [fundamentals.md](fundamentals.md)
