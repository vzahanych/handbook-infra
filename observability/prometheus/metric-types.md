# Prometheus — metric types

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Counters and gauges](#1-counters-and-gauges)
  * [2. Histograms](#2-histograms)
  * [3. Summaries](#3-summaries)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Prometheus has four metric types, and choosing the right one is fundamental to useful monitoring. A counter only ever increases and is used for totals like requests served, queried with `rate()` to get per-second rates. A gauge can go up or down and represents a current value like memory in use or queue depth.

A histogram samples observations into configurable buckets, letting you compute quantiles like latency percentiles across many instances, while a summary computes quantiles client-side. Picking counter versus gauge versus histogram correctly determines what questions you can later answer.

---

## Detailed explanation with examples

### 1. Counters and gauges

- TODO: counter (monotonic, use `rate()`) vs gauge (current value)

### 2. Histograms

- TODO: buckets; `histogram_quantile`; aggregatable across instances

### 3. Summaries

- TODO: client-side quantiles; not aggregatable across instances

### 4. Practical rule

```text
Counter for totals (rate it), gauge for current values, histogram for percentiles.
Prefer histograms over summaries when you aggregate across instances.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: name counters with `_total`; choose histogram buckets to match SLOs

### Operations and production

- TODO: watch histogram bucket cardinality; avoid summaries for fleet-wide quantiles

## References

- Official docs: https://prometheus.io/docs/concepts/metric_types/
- Overview: [fundamentals.md](fundamentals.md)
