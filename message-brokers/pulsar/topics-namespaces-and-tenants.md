# Pulsar — topics, namespaces, and tenants

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The three-part hierarchy](#1-the-three-part-hierarchy)
  * [2. Namespace policies](#2-namespace-policies)
  * [3. Partitioned topics](#3-partitioned-topics)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Pulsar organizes topics under a three-part hierarchy: a tenant contains namespaces, and a namespace contains topics, addressed as `persistent://tenant/namespace/topic`. This structure exists for multi-tenancy, letting different teams or applications share a cluster with isolation and per-namespace policies for retention, quotas, and access.

Topics can be partitioned for parallelism much like Kafka, or kept as single non-partitioned topics. Designing the tenant and namespace layout up front is how you map organizational boundaries onto the cluster.

---

## Detailed explanation with examples

### 1. The three-part hierarchy

- TODO: `persistent://tenant/namespace/topic`; persistent vs non-persistent

### 2. Namespace policies

- TODO: retention, quotas, auth set per namespace

### 3. Partitioned topics

- TODO: partitions for parallelism (Kafka-like)

### 4. Practical rule

```text
Map tenants/namespaces to org boundaries; set policies per namespace.
Partition topics for parallelism when needed.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: choose partitioned vs non-partitioned by ordering/parallelism needs

### Operations and production

- TODO: apply isolation and quota policies per namespace/tenant

## References

- Official docs: https://pulsar.apache.org/docs/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [producers-and-subscriptions.md](producers-and-subscriptions.md)
