# Kafka — brokers, replication, and the controller

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Brokers and partition leaders](#1-brokers-and-partition-leaders)
  * [2. Replication and the ISR](#2-replication-and-the-isr)
  * [3. The controller: KRaft and ZooKeeper](#3-the-controller-kraft-and-zookeeper)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

A Kafka cluster is a set of brokers, and each partition has one leader broker that handles its reads and writes plus follower replicas on other brokers that copy the data. The set of replicas that are fully caught up is the in-sync replica set (ISR), and a write counts as durable once the required number of in-sync replicas have it.

Cluster metadata — which broker leads which partition — is coordinated by the controller, historically through ZooKeeper but now through the built-in KRaft consensus in modern Kafka. Replication factor and `min.insync.replicas` together set how many failures the cluster tolerates without losing data or availability.

---

## Detailed explanation with examples

### 1. Brokers and partition leaders

- TODO: leader handles I/O; followers replicate
- TODO: leader election on failure

### 2. Replication and the ISR

- TODO: replication factor; in-sync replica set
- TODO: `min.insync.replicas` vs `acks=all`

### 3. The controller: KRaft and ZooKeeper

- TODO: ZooKeeper (legacy) vs KRaft (modern)
- TODO: metadata and controller role

### 4. Practical rule

```text
RF ≥ 3 and min.insync.replicas ≥ 2 for durability without single-point loss.
Prefer KRaft on new clusters.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: pair `acks=all` with `min.insync.replicas` ≥ 2

### Operations and production

- TODO: RF ≥ 3; spread replicas across racks/AZs
- TODO: monitor under-replicated partitions and ISR shrink/expand

## References

- Official docs: https://kafka.apache.org/documentation/
- Overview: [fundamentals.md](fundamentals.md)
