# Cassandra — keyspaces and the ring

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Keyspaces as the top namespace](#1-keyspaces-as-the-top-namespace)
  * [2. Tokens and the ring](#2-tokens-and-the-ring)
  * [3. Replication strategy on the keyspace](#3-replication-strategy-on-the-keyspace)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

A keyspace is Cassandra's top-level container, the place where tables live and where you set the replication strategy that decides how many copies of the data exist and in which datacenters. Below that, the cluster is organized as a ring: each node owns a range of token values, and the partition key of every row is hashed to a token that places the row on the nodes responsible for that range.

Because placement follows the hash rather than any insertion order, data spreads across the ring on its own, and adding nodes reassigns token ranges instead of reshaping the schema. The keyspace is therefore where distribution policy lives, while the ring is the mechanism that carries it out.

---

## Detailed explanation with examples

### 1. Keyspaces as the top namespace

- TODO: `CREATE KEYSPACE`; keyspace → table hierarchy
- TODO: one keyspace per application/bounded context
- TODO: system keyspaces

### 2. Tokens and the ring

- TODO: token ranges and ownership
- TODO: virtual nodes (vnodes)
- TODO: partitioner (Murmur3) and how keys map to tokens

### 3. Replication strategy on the keyspace

- TODO: `SimpleStrategy` vs `NetworkTopologyStrategy`
- TODO: replication factor per datacenter
- TODO: snitches and rack/DC awareness

### 4. Practical rule

```text
Use NetworkTopologyStrategy from day one, even in a single DC.
Let the ring spread data; never encode placement into keys yourself.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: one keyspace per service; do not share across teams
- TODO: choose RF per DC deliberately (commonly 3)

### Operations and production

- TODO: keep vnode counts and snitch config consistent across nodes
- TODO: plan token ranges before adding/removing nodes; run cleanup after

## References

- Official docs: https://cassandra.apache.org/doc/
- Overview: [fundamentals.md](fundamentals.md)
