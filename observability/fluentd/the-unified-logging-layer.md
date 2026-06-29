# Fluentd — the unified logging layer

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Decoupling producers and consumers](#1-decoupling-producers-and-consumers)
  * [2. A common event format](#2-a-common-event-format)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Fluentd's guiding idea is the unified logging layer: rather than every application talking directly to every storage system, all logs flow through Fluentd, which decouples producers from consumers. Applications and agents send data in, Fluentd normalizes it into a common event format, and outputs deliver it wherever it needs to go, so adding a new destination is a config change rather than an application change.

This decoupling is what makes log architecture maintainable as sources and sinks multiply. It is the conceptual reason Fluentd sits in the middle.

---

## Detailed explanation with examples

### 1. Decoupling producers and consumers

- TODO: apps → Fluentd → many sinks; add a sink via config

### 2. A common event format

- TODO: tag + time + record normalization

### 3. Practical rule

```text
Route all logs through one layer; add destinations by config, not code.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: normalize to a common schema at the layer

### Operations and production

- TODO: treat the aggregator as critical infrastructure (HA, capacity)

## References

- Official docs: https://docs.fluentd.org/
- Overview: [fundamentals.md](fundamentals.md)
