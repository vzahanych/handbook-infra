# Redpanda — differences from Kafka

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. No JVM, no ZooKeeper](#1-no-jvm-no-zookeeper)
  * [2. Thread-per-core and a single binary](#2-thread-per-core-and-a-single-binary)
  * [3. Tooling and self-tuning](#3-tooling-and-self-tuning)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Although Redpanda is Kafka-compatible at the API level, the implementation differences are the reason to choose it. There is no JVM, so there is no garbage-collection tuning and latency is more predictable; there is no ZooKeeper or separate controller quorum, since Raft handles everything; and a thread-per-core architecture uses modern hardware efficiently.

Operationally it ships as a single binary, which simplifies deployment, and it self-tunes much of what Kafka exposes as knobs. Treat it as Kafka for application design, but verify version-specific API coverage and learn its own operational tooling.

---

## Detailed explanation with examples

### 1. No JVM, no ZooKeeper

- TODO: predictable latency; no GC tuning; no external coordinator

### 2. Thread-per-core and a single binary

- TODO: shard-per-core; simple deployment

### 3. Tooling and self-tuning

- TODO: `rpk`, Redpanda Console; auto-tuning

### 4. Practical rule

```text
Kafka for app design; verify API coverage; learn rpk and let it self-tune.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: don't assume every newest Kafka feature exists

### Operations and production

- TODO: use `rpk`/Console; rely on auto-tuning over manual JVM-style knobs

## References

- Official docs: https://docs.redpanda.com/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [../kafka/fundamentals.md](../kafka/fundamentals.md)
