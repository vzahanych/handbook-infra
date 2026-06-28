# NATS — clustering and scaling

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Clusters](#1-clusters)
  * [2. Superclusters and leaf nodes](#2-superclusters-and-leaf-nodes)
  * [3. JetStream replication](#3-jetstream-replication)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

NATS scales by clustering servers that gossip and route messages to each other, so subscribers on any server receive messages published anywhere in the cluster. For wide deployments, superclusters and leaf nodes connect clusters across regions and edge locations while keeping a single logical namespace.

JetStream adds replication, storing each stream on a configurable number of nodes via the Raft protocol for durability and failover. The design favors a flat, always-connected mesh, so scaling is largely about adding servers and placing streams with the right replication.

---

## Detailed explanation with examples

### 1. Clusters

- TODO: full-mesh servers; message routing across nodes

### 2. Superclusters and leaf nodes

- TODO: gateways across regions; leaf nodes at the edge

### 3. JetStream replication

- TODO: stream replicas (R1/R3/R5) via Raft

### 4. Practical rule

```text
Scale core NATS by adding servers; replicate JetStream streams (R3) for HA.
Use leaf nodes for edge; superclusters across regions.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: choose stream replica count by durability needs

### Operations and production

- TODO: place stream replicas across AZs; monitor Raft/leadership and storage

## References

- Official docs: https://docs.nats.io/
- Overview: [fundamentals.md](fundamentals.md)
