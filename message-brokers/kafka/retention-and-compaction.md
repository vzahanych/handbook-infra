# Kafka — retention and compaction

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Time and size retention](#1-time-and-size-retention)
  * [2. Log compaction](#2-log-compaction)
  * [3. Choosing a cleanup policy](#3-choosing-a-cleanup-policy)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Kafka keeps records independently of whether they have been consumed, and retention decides how long. The default policy deletes whole log segments once they pass a time or size limit, which suits event streams where old data simply ages out. Consumers can replay anything still within the retention window.

The alternative policy is log compaction, which keeps only the latest record for each key and discards older versions, turning a topic into a changelog of current state. Compaction is what lets a topic act as a durable key-value snapshot — the basis for patterns like Kafka Streams state stores — rather than a time-bounded stream.

---

## Detailed explanation with examples

### 1. Time and size retention

- TODO: `retention.ms`, `retention.bytes`; segment deletion

### 2. Log compaction

- TODO: `cleanup.policy=compact`; latest value per key
- TODO: tombstones for deletes

### 3. Choosing a cleanup policy

- TODO: delete (streams) vs compact (changelogs/state)
- TODO: combining `compact,delete`

### 4. Practical rule

```text
Use delete retention for event streams; compaction for keyed state/changelogs.
Set retention so consumers can recover within the window.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: design keys for compacted topics; emit tombstones to delete keys

### Operations and production

- TODO: size retention vs disk; monitor log cleaner and disk usage

## References

- Official docs: https://kafka.apache.org/documentation/
- Overview: [fundamentals.md](fundamentals.md)
