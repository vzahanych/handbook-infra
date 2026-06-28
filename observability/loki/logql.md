# Loki — LogQL

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Stream selectors](#1-stream-selectors)
  * [2. Line filters and parsers](#2-line-filters-and-parsers)
  * [3. Metrics from logs](#3-metrics-from-logs)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

LogQL is Loki's query language, and it works in two stages that mirror the data model. First a log stream selector picks streams by label using matchers like `{app="api", env="prod"}`; then line filters and parsers operate on the selected lines, searching for substrings and parsing JSON or logfmt to extract fields.

LogQL can also produce metrics from logs, wrapping a log query in functions like `rate()` or `count_over_time()` to graph log-derived rates alongside real metrics. Always starting with a tight label selector is what keeps queries fast, since everything after it is a scan.

---

## Detailed explanation with examples

### 1. Stream selectors

- TODO: `{label="value"}` matchers; the narrower the better

### 2. Line filters and parsers

- TODO: `|= "err"`, `!=`, regex; `| json`, `| logfmt`; label extraction

### 3. Metrics from logs

- TODO: `rate()`, `count_over_time()` over a log query

### 4. Practical rule

```text
Start with a tight {label} selector; then filter/parse lines.
Derive metrics from logs with rate()/count_over_time().
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: always constrain by label first; parse fields at query time

### Operations and production

- TODO: watch unbounded queries (wide selector + long range)

## References

- Official docs: https://grafana.com/docs/loki/latest/query/
- Overview: [fundamentals.md](fundamentals.md)
