# Prometheus — labels and the data model

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Series identity](#1-series-identity)
  * [2. Cardinality](#2-cardinality)
  * [3. Relabeling](#3-relabeling)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Every Prometheus time series is uniquely identified by its metric name plus a set of key-value labels, and this multi-dimensional model is the core of how Prometheus works. Labels let one metric like `http_requests_total` carry dimensions such as method, status, and handler, which you then filter and aggregate over in queries.

The catch is cardinality: each distinct combination of label values is a separate series, so putting high-variety values like user IDs or request IDs into labels causes a cardinality explosion that overwhelms memory and storage. Keeping label values bounded and low-cardinality is the central discipline.

---

## Detailed explanation with examples

### 1. Series identity

- TODO: metric name + labels = unique series

### 2. Cardinality

- TODO: each label-value combo is a series; explosion from high-variety labels

### 3. Relabeling

- TODO: relabel_configs / metric_relabel_configs to drop or reshape labels

### 4. Practical rule

```text
Use labels for bounded dimensions; never label by id/request/email.
Drop high-cardinality labels with relabeling at scrape time.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: keep label sets small and bounded; standardize label names

### Operations and production

- TODO: monitor series count; alert on cardinality spikes; drop offending labels

## References

- Official docs: https://prometheus.io/docs/concepts/data_model/
- Overview: [fundamentals.md](fundamentals.md)
