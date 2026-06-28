# Alertmanager — alerts from Prometheus

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Alerts are pushed in](#1-alerts-are-pushed-in)
  * [2. Labels and annotations](#2-labels-and-annotations)
  * [3. Firing and resolved](#3-firing-and-resolved)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Alertmanager does not evaluate metrics itself; it receives already-fired alerts pushed from one or more Prometheus servers. An alert arrives as a set of labels and annotations — the labels identify and classify it, the annotations carry human-readable detail — and the same labels are what Alertmanager matches on for routing and grouping.

An alert has a lifecycle: it is firing while the condition holds and resolved when it clears, and Alertmanager can notify on both. Understanding that alerts are label-carrying objects pushed in is the basis for everything Alertmanager does.

---

## Detailed explanation with examples

### 1. Alerts are pushed in

- TODO: Prometheus evaluates rules and pushes alerts

### 2. Labels and annotations

- TODO: labels classify/route; annotations carry detail

### 3. Firing and resolved

- TODO: lifecycle; resolve notifications

### 4. Practical rule

```text
Design alert labels for routing/grouping; put human detail in annotations.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: standardize labels (severity, team, service) for routing

### Operations and production

- TODO: decide whether to notify on resolved; keep label schemes consistent

## References

- Official docs: https://prometheus.io/docs/alerting/latest/alertmanager/
- Overview: [fundamentals.md](fundamentals.md)
