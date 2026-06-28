# Kafka — consumers and consumer groups

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Consumer groups and partition assignment](#1-consumer-groups-and-partition-assignment)
  * [2. Rebalancing](#2-rebalancing)
  * [3. Scaling reads](#3-scaling-reads)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Consumers read partitions, and they cooperate through consumer groups: within a group, each partition is assigned to exactly one consumer, so the group as a whole processes the topic in parallel without duplicating work. Adding consumers up to the partition count increases throughput, but consumers beyond that count sit idle because there are no spare partitions to assign.

Different groups are independent, each maintaining its own position in the log, which is how the same topic feeds many separate applications at once. When membership changes, the group rebalances partition assignments, briefly pausing consumption.

---

## Detailed explanation with examples

### 1. Consumer groups and partition assignment

- TODO: one partition → one consumer within a group
- TODO: independent groups each track their own offsets

### 2. Rebalancing

- TODO: triggers (join/leave/failure); stop-the-world vs cooperative
- TODO: session timeout, heartbeat, poll interval

### 3. Scaling reads

- TODO: consumers ≤ partitions for parallelism
- TODO: idle consumers beyond partition count

### 4. Practical rule

```text
Max useful consumers per group = partition count.
Keep processing within the poll interval to avoid rebalances.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: make processing idempotent; commit offsets after successful work
- TODO: use cooperative rebalancing to reduce stop-the-world pauses

### Operations and production

- TODO: monitor consumer lag and rebalance frequency
- TODO: tune `max.poll.records`/timeouts to processing time

## References

- Official docs: https://kafka.apache.org/documentation/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [offsets-and-delivery-semantics.md](offsets-and-delivery-semantics.md)
