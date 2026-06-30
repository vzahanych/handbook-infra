# OpenTelemetry — signals: traces, metrics, logs

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The three signals](#1-the-three-signals)
  * [2. One correlated model](#2-one-correlated-model)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

OpenTelemetry models observability as a set of signals that share one consistent interface and one data model. A signal is simply a category of telemetry, and the three primary ones are traces, metrics, and logs, joined by baggage and the emerging events and profiles. What makes OpenTelemetry valuable is not any single signal but the decision to treat them together, so they share the same context and attributes.

Traces describe behavior over time. A trace follows one request as it travels through your system, and it is built from spans, where each span is a single unit of work with a start time, a duration, and attributes. Strung together, the spans of a trace show you exactly where a request spent its time and where it failed.

Metrics describe magnitude. A metric is a numeric measurement captured repeatedly at runtime, such as a counter that only goes up, a gauge that rises and falls, or a histogram that buckets a distribution of values. Metrics are cheap to store and ideal for dashboards and alerts because they aggregate cleanly across many requests.

Logs describe individual events. A log is a timestamped record of something that happened, often a line of text with structured fields attached. In OpenTelemetry a log can carry the trace and span identifiers of the request that produced it, which is what turns a wall of log lines into something you can pivot through.

The real point is correlation. Because every signal flows through the same libraries and the same protocol and carries the same context, a single trace identifier can tie a slow span to the metrics and logs around it. Understanding the signals as one connected whole, rather than three separate tools, is the core OpenTelemetry idea.

---

## Detailed explanation with examples

### 1. The three signals

- TODO: traces (spans), metrics (measurements), logs (events)

### 2. One correlated model

- TODO: shared context/attributes; trace ID linking signals

### 3. Practical rule

```text
Treat traces, metrics, and logs as one correlated set, not three silos.
Share context so you can pivot between them.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: attach trace context to logs and exemplars to metrics

### Operations and production

- TODO: route each signal to the right backend while keeping correlation

## References

- Official docs: https://opentelemetry.io/docs/concepts/signals/
- Per-signal cards: [signal-traces.md](signal-traces.md), [signal-metrics.md](signal-metrics.md), [signal-logs.md](signal-logs.md), [signal-baggage.md](signal-baggage.md), [signal-events.md](signal-events.md), [signal-profiles.md](signal-profiles.md)
- Overview: [fundamentals.md](fundamentals.md)
