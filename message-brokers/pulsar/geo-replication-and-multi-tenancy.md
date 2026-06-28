# Pulsar — geo-replication and multi-tenancy

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Multi-tenancy](#1-multi-tenancy)
  * [2. Geo-replication](#2-geo-replication)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Two of Pulsar's headline features come almost for free from its architecture: multi-tenancy and geo-replication. The tenant-and-namespace hierarchy, combined with per-namespace policies and authentication, lets many teams share one cluster safely, which is why Pulsar is common as shared infrastructure.

Geo-replication asynchronously copies messages in a namespace between clusters in different regions, so producers and consumers in each region work locally while data converges globally. Both are configured as policies rather than built by hand, making cross-region and multi-team setups a matter of configuration.

---

## Detailed explanation with examples

### 1. Multi-tenancy

- TODO: tenant/namespace isolation; per-tenant auth and quotas

### 2. Geo-replication

- TODO: async cross-cluster replication per namespace; conflict/ordering notes

### 3. Practical rule

```text
Isolate teams with tenants/namespaces; enable geo-replication per namespace.
Both are configuration, not custom plumbing.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: design for async cross-region convergence (eventual, per-region local)

### Operations and production

- TODO: enforce per-tenant auth/quotas; monitor replication backlog/lag

## References

- Official docs: https://pulsar.apache.org/docs/
- Overview: [fundamentals.md](fundamentals.md)
