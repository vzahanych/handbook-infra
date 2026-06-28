# Tempo — metrics and correlation

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Exemplars and log links](#1-exemplars-and-log-links)
  * [2. Span-derived metrics](#2-span-derived-metrics)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Tempo's real power shows up when traces are linked to the other signals in a Grafana stack. Exemplars let a Prometheus metric point to example trace IDs, so a latency spike on a graph links straight to a representative slow trace; log lines in Loki can carry the trace ID for the same jump from logs to traces.

Tempo can also generate metrics from spans, such as request rates and latencies derived from trace data, feeding them back to Prometheus. This correlation across metrics, logs, and traces is the whole point of running Tempo alongside Prometheus and Loki.

---

## Detailed explanation with examples

### 1. Exemplars and log links

- TODO: Prometheus exemplars → trace; Loki line → trace ID

### 2. Span-derived metrics

- TODO: metrics-generator: rates/latencies from spans

### 3. Practical rule

```text
Wire metrics→traces (exemplars) and logs→traces (trace ID) in Grafana.
Use span-derived metrics to spot what to drill into.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: include trace IDs in logs; enable exemplars on histograms

### Operations and production

- TODO: enable the metrics-generator if you want RED metrics from traces

## References

- Official docs: https://grafana.com/docs/tempo/latest/
- Overview: [fundamentals.md](fundamentals.md)
