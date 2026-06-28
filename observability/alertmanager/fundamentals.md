# Alertmanager — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Alerts from Prometheus](#1-alerts-from-prometheus)
  * [2. The routing tree](#2-the-routing-tree)
  * [3. Grouping, inhibition, and silences](#3-grouping-inhibition-and-silences)
  * [4. Receivers and notifications](#4-receivers-and-notifications)
  * [5. High availability](#5-high-availability)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Alertmanager is the component that takes alerts fired by Prometheus and turns them into the right notifications to the right people. Prometheus decides when something is wrong and sends an alert; Alertmanager decides what to do with it — how to group related alerts, where to route them, when to stay quiet, and which channel to notify. This separation keeps alert logic in Prometheus and notification logic in Alertmanager.

Its core mechanisms are a routing tree that matches alerts by label to receivers, grouping that batches related alerts into one notification, inhibition and silences that suppress noise, and receivers that deliver to email, Slack, PagerDuty, and others. For reliability it runs as a small cluster that deduplicates so a notification is sent once even with multiple instances.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Alerts from Prometheus

How alerts arrive as label-carrying objects with a firing/resolved lifecycle. See [alerts-from-prometheus.md](alerts-from-prometheus.md).

### 2. The routing tree

Matching alerts by label down a tree to receivers and timing. See [the-routing-tree.md](the-routing-tree.md).

### 3. Grouping, inhibition, and silences

Batching, suppression, and temporary mutes to control noise. See [grouping-inhibition-and-silences.md](grouping-inhibition-and-silences.md).

### 4. Receivers and notifications

Delivery integrations and templated notification content. See [receivers-and-notifications.md](receivers-and-notifications.md).

### 5. High availability

Clustered, gossiping Alertmanagers that deduplicate notifications. See [high-availability.md](high-availability.md).

### 6. Practical rule

```text
Prometheus fires; Alertmanager routes, groups, silences, and notifies.
Encode ownership in the routing tree by label; run a clustered pair.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: route by labels (team/severity/env); group to avoid alert floods
- TODO: use inhibition + silences for known/maintenance noise

### Operations and production

- TODO: run ≥ 2 clustered instances; point all Prometheus servers at all of them
- TODO: test receivers; tune group/repeat intervals to balance promptness vs spam

## References

- Official docs: https://prometheus.io/docs/alerting/latest/alertmanager/
- Related: [../prometheus/fundamentals.md](../prometheus/fundamentals.md)
