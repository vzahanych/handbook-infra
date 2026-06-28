# Prometheus — PromQL basics

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Selectors and vectors](#1-selectors-and-vectors)
  * [2. Rate and range functions](#2-rate-and-range-functions)
  * [3. Aggregation by labels](#3-aggregation-by-labels)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

PromQL is the query language for selecting and computing over time series. A basic query selects series by metric name and label matchers, returning an instant vector of current values, while a range selector returns a range vector of samples over a window for use with functions.

The most common pattern is `rate(metric[5m])` to turn a counter into a per-second rate, then aggregation operators like `sum`, `avg`, and `by` to roll up across labels. Learning to combine selectors, rate functions, and aggregation by labels is what turns raw metrics into answers.

---

## Detailed explanation with examples

### 1. Selectors and vectors

- TODO: label matchers; instant vs range vectors

### 2. Rate and range functions

- TODO: `rate`/`irate`/`increase` over `[window]`

### 3. Aggregation by labels

- TODO: `sum/avg/max by (...)`; `histogram_quantile`

### 4. Practical rule

```text
rate(counter[5m]) then sum by (...) is the workhorse pattern.
Match the rate window to ~4x the scrape interval.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: rate counters before aggregating; aggregate with explicit `by`

### Operations and production

- TODO: precompute heavy queries as recording rules

## References

- Official docs: https://prometheus.io/docs/prometheus/latest/querying/basics/
- Overview: [fundamentals.md](fundamentals.md)
