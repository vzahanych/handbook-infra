# ActiveMQ Artemis — clustering and high availability

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Clustering](#1-clustering)
  * [2. Live and backup pairing](#2-live-and-backup-pairing)
  * [3. Shared-store versus replication](#3-shared-store-versus-replication)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

For scale and resilience Artemis runs as a cluster of brokers that share load by distributing messages among themselves, so consumers on any node can be served. High availability is provided by pairing brokers: a live broker has a backup that takes over on failure, using either shared storage, where both access the same journal, or replication, where the backup keeps a synchronized copy over the network.

Choosing shared-store versus replication, and configuring failover, is the main HA decision. Clustering plus a backup pairing is how Artemis avoids a single broker being a point of failure.

---

## Detailed explanation with examples

### 1. Clustering

- TODO: brokers share load; message redistribution

### 2. Live and backup pairing

- TODO: backup takes over on live failure; failover/failback

### 3. Shared-store versus replication

- TODO: shared journal vs network replication; trade-offs

### 4. Practical rule

```text
Cluster for load; pair live/backup for HA.
Shared-store needs reliable shared storage; replication needs a fast network + quorum.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: use HA-aware client connection/failover settings

### Operations and production

- TODO: pick shared-store vs replication deliberately; test failover/failback; avoid split-brain

## References

- Official docs: https://activemq.apache.org/components/artemis/documentation/
- Overview: [fundamentals.md](fundamentals.md)
