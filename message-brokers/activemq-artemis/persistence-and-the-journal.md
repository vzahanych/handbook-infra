# ActiveMQ Artemis — persistence and the journal

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The append-only journal](#1-the-append-only-journal)
  * [2. Compaction](#2-compaction)
  * [3. Paging](#3-paging)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Artemis achieves durability through an append-only journal rather than a general database, which is a large part of why it is fast. Persistent messages are written sequentially to journal files, an operation that suits disks well, and the broker periodically compacts the journal to reclaim space from acknowledged messages.

You can choose the journal implementation, with options like Linux AIO for high throughput, and configure paging so that when a queue's memory fills, messages spill to disk instead of overwhelming the broker. Understanding the journal and paging is central to tuning Artemis for both speed and large backlogs.

---

## Detailed explanation with examples

### 1. The append-only journal

- TODO: sequential writes; AIO vs NIO journal types

### 2. Compaction

- TODO: reclaiming space from acknowledged messages

### 3. Paging

- TODO: spilling to disk when address memory fills

### 4. Practical rule

```text
Use AIO journal on Linux for throughput; enable paging to survive large backlogs.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: mark messages persistent only when durability is required

### Operations and production

- TODO: put the journal on fast disks; tune paging thresholds; monitor disk/journal

## References

- Official docs: https://activemq.apache.org/components/artemis/documentation/
- Overview: [fundamentals.md](fundamentals.md)
