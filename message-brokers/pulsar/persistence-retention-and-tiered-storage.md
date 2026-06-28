# Pulsar — persistence, retention, and tiered storage

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Durable by default](#1-durable-by-default)
  * [2. Retention and backlog quotas](#2-retention-and-backlog-quotas)
  * [3. Tiered storage](#3-tiered-storage)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Pulsar persists messages durably in BookKeeper by default, and how long they are kept is governed by retention and backlog policies set per namespace. Once all subscriptions have acknowledged a message it becomes eligible for deletion, but a retention policy can keep acknowledged messages around for replay, and a backlog quota bounds unacknowledged buildup.

For long-term, low-cost storage, tiered storage offloads older segments from BookKeeper to object stores like S3 while keeping them queryable. Together these let a topic act as both a short-term queue and a long-term event store.

---

## Detailed explanation with examples

### 1. Durable by default

- TODO: persistent topics stored in BookKeeper

### 2. Retention and backlog quotas

- TODO: ack-then-delete; retention for replay; backlog quota limits

### 3. Tiered storage

- TODO: offload old segments to S3/GCS; still readable

### 4. Practical rule

```text
Set retention to enable replay; bound backlog to protect storage.
Offload cold data to object storage for cheap long-term retention.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: rely on retention for replay rather than re-publishing

### Operations and production

- TODO: configure retention + backlog quota per namespace; enable tiered offload

## References

- Official docs: https://pulsar.apache.org/docs/
- Overview: [fundamentals.md](fundamentals.md)
