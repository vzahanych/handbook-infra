# Vector — the event model

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Logs, metrics, traces](#1-logs-metrics-traces)
  * [2. Metrics as first-class events](#2-metrics-as-first-class-events)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Vector treats everything as events, and it natively understands three event types: logs, metrics, and traces. A log event is a structured record of fields, a metric event is a typed measurement like a counter or gauge, and traces are supported as their own type, so one pipeline can carry and convert between signal types.

Because metrics are first-class rather than just text, Vector can aggregate and transform them, and even derive metrics from logs. Understanding that the pipeline carries typed events, not just log lines, is what unlocks its more advanced uses.

---

## Detailed explanation with examples

### 1. Logs, metrics, traces

- TODO: log = structured record; metric = typed measurement; traces

### 2. Metrics as first-class events

- TODO: aggregate/transform metrics; `log_to_metric`

### 3. Practical rule

```text
The pipeline carries typed events, not just lines.
Exploit first-class metrics: aggregate, convert, derive from logs.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: keep log events structured; use metric events for measurements

### Operations and production

- TODO: derive metrics from logs to reduce downstream volume where useful

## References

- Official docs: https://vector.dev/docs/about/under-the-hood/architecture/data-model/
- Overview: [fundamentals.md](fundamentals.md)
