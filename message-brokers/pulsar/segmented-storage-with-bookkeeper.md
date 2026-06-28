# Pulsar — segmented storage with BookKeeper

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Stateless brokers](#1-stateless-brokers)
  * [2. Segments and bookies](#2-segments-and-bookies)
  * [3. Elastic scaling and failover](#3-elastic-scaling-and-failover)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Underneath, a Pulsar topic is not stored by the broker but as a log of segments in Apache BookKeeper, where each segment is replicated across several bookie nodes. Because the log is split into many segments spread across the storage cluster, a single topic is not bound by one node's capacity and can grow far beyond it, and recovery after a failure only needs to re-replicate segments rather than whole topics.

Brokers stay stateless, holding only a cursor and cache, so they can fail over instantly by pointing at the same BookKeeper data. This segment-based design is what gives Pulsar its elastic scaling and fast failover.

---

## Detailed explanation with examples

### 1. Stateless brokers

- TODO: brokers serve, BookKeeper stores; instant broker failover

### 2. Segments and bookies

- TODO: topic = segments; ensemble/write/ack quorum across bookies

### 3. Elastic scaling and failover

- TODO: topic not bound to one node; re-replicate segments on failure

### 4. Practical rule

```text
Scale brokers (stateless) and bookies (storage) independently.
Durability comes from BookKeeper quorums, not the broker.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: rely on broker statelessness; don't pin clients to a broker

### Operations and production

- TODO: tune ensemble/write/ack quorum; spread bookies across AZs; monitor bookie health

## References

- Official docs: https://pulsar.apache.org/docs/
- Overview: [fundamentals.md](fundamentals.md)
