# Alertmanager — high availability

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Clustered gossip](#1-clustered-gossip)
  * [2. Deduplication](#2-deduplication)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Alertmanager is meant to run as a small cluster rather than a single instance, because a missed notification can mean a missed incident. The instances gossip about which notifications they have sent, so even when several Prometheus servers send the same alert to several Alertmanagers, the alert is deduplicated and the notification goes out once.

This design tolerates the loss of an instance without dropping or duplicating pages. Running at least two clustered Alertmanagers, fed by Prometheus's list of all of them, is the standard reliable setup.

---

## Detailed explanation with examples

### 1. Clustered gossip

- TODO: `--cluster.*` peers; gossip of notification state

### 2. Deduplication

- TODO: all Prometheis send to all AMs; dedup → one notification

### 3. Practical rule

```text
Run ≥ 2 clustered Alertmanagers; configure Prometheus with all of them.
The cluster deduplicates so each alert pages once.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: point every Prometheus at the full Alertmanager set

### Operations and production

- TODO: spread instances across nodes/AZs; monitor cluster peer health

## References

- Official docs: https://prometheus.io/docs/alerting/latest/alertmanager/
- Overview: [fundamentals.md](fundamentals.md)
