# Prometheus — recording and alerting rules

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Recording rules](#1-recording-rules)
  * [2. Alerting rules and `for`](#2-alerting-rules-and-for)
  * [3. Handing off to Alertmanager](#3-handing-off-to-alertmanager)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Rules let Prometheus evaluate PromQL on a schedule instead of only on demand. A recording rule precomputes an expensive or frequently-used query and saves the result as a new time series, which speeds up dashboards and keeps queries simple.

An alerting rule evaluates a condition and, when it holds for a configured duration, fires an alert that Prometheus sends to Alertmanager for routing and notification. The `for` duration prevents flapping by requiring a condition to persist before alerting, turning passive metrics into proactive monitoring.

---

## Detailed explanation with examples

### 1. Recording rules

- TODO: precompute series; naming conventions (`level:metric:operation`)

### 2. Alerting rules and `for`

- TODO: condition + `for` duration; labels/annotations

### 3. Handing off to Alertmanager

- TODO: Prometheus fires; Alertmanager routes/notifies

### 4. Practical rule

```text
Recording rules for expensive/reused queries; alerting rules with a `for` to avoid flaps.
Prometheus decides when to fire; Alertmanager decides who to tell.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: add `for` durations; attach meaningful labels/annotations to alerts

### Operations and production

- TODO: version rules as code; monitor rule evaluation failures/latency

## References

- Official docs: https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [../alertmanager/fundamentals.md](../alertmanager/fundamentals.md)
