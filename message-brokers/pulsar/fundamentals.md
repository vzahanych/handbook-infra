# Pulsar — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Topics, namespaces, and tenants](#1-topics-namespaces-and-tenants)
  * [2. Producers and subscriptions](#2-producers-and-subscriptions)
  * [3. Segmented storage with BookKeeper](#3-segmented-storage-with-bookkeeper)
  * [4. Persistence, retention, and tiered storage](#4-persistence-retention-and-tiered-storage)
  * [5. Geo-replication and multi-tenancy](#5-geo-replication-and-multi-tenancy)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Apache Pulsar is a distributed pub-sub and streaming platform that separates serving from storage. Producers publish to topics, organized under a two-level hierarchy of tenants and namespaces for multi-tenancy, and consumers attach through named subscriptions whose type decides how messages are shared among them. Brokers handle the messaging but do not store data themselves; they delegate to Apache BookKeeper, which keeps each topic as a sequence of replicated segments.

This separation of compute and storage is Pulsar's defining trait: brokers are stateless and can be scaled or replaced freely, while BookKeeper scales storage independently and enables features like tiered offload to object storage and built-in geo-replication. The subscription model also blends queueing and streaming in one system, depending on the subscription type you choose.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Topics, namespaces, and tenants

The tenant/namespace/topic hierarchy for multi-tenancy and partitioning. See [topics-namespaces-and-tenants.md](topics-namespaces-and-tenants.md).

### 2. Producers and subscriptions

Subscriptions and their types (exclusive, failover, shared, key_shared). See [producers-and-subscriptions.md](producers-and-subscriptions.md).

### 3. Segmented storage with BookKeeper

How topics are stored as replicated segments in BookKeeper, with stateless brokers. See [segmented-storage-with-bookkeeper.md](segmented-storage-with-bookkeeper.md).

### 4. Persistence, retention, and tiered storage

Durability, retention/backlog policies, and offload to object storage. See [persistence-retention-and-tiered-storage.md](persistence-retention-and-tiered-storage.md).

### 5. Geo-replication and multi-tenancy

Per-namespace multi-tenancy and cross-region geo-replication. See [geo-replication-and-multi-tenancy.md](geo-replication-and-multi-tenancy.md).

### 6. Practical rule

```text
Choose the subscription type to get a queue or an ordered stream from one topic.
Lean on compute/storage separation: scale brokers and BookKeeper independently.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: pick subscription type per consumer need; key_shared for ordered sharing
- TODO: lay out tenants/namespaces to match team/app boundaries

### Operations and production

- TODO: size BookKeeper ensemble/write quorum for durability
- TODO: set retention/backlog quotas; use tiered storage for long-term data

## References

- Official docs: https://pulsar.apache.org/docs/
- Related: [../kafka/fundamentals.md](../kafka/fundamentals.md)
