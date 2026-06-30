# OpenTelemetry — metrics

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Instruments](#1-instruments)
  * [2. Aggregation and temporality](#2-aggregation-and-temporality)
  * [3. Exemplars](#3-exemplars)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

A metric is a numeric measurement captured repeatedly while your application runs. Where a trace describes one request in detail, a metric describes many requests in aggregate, by reducing them to numbers like a request count, an error rate, or a queue depth. It is the signal you reach for when you want to know the overall health and shape of a system rather than the fate of any single call.

Metrics are produced through instruments, and the kind of instrument you choose reflects the kind of number you are measuring. A counter only ever goes up and suits things you tally, such as the number of requests served. A gauge can rise and fall and suits things you sample, such as memory in use right now. A histogram records a distribution of values, such as request durations, so you can later ask about the median or the slowest few percent.

The numbers are not stored one per event but combined as they are collected, which is what makes metrics so cheap. This combining is called aggregation, and a related choice called temporality decides whether each reported value is a running total since the start or only the change since the last report. These choices matter because they determine how a backend like Prometheus should interpret and add up the data.

Metrics aggregate away the individual requests, but you often still want a way back to an example, and that is what exemplars provide. An exemplar attaches the trace identifier of a representative request to a metric data point, so that a spike in a latency histogram can lead you directly to one of the slow traces behind it. This is one of the concrete payoffs of carrying all the signals in a single system.

What metrics are best at is breadth at low cost. Because they summarize rather than record everything, they are ideal for the dashboards you watch and the alerts that page you, and they stay affordable even at very high request rates. The discipline they demand is care with labels, since attaching high-cardinality values like user identifiers to a metric can multiply its storage cost enormously.

---

## Detailed explanation with examples

### 1. Instruments

- TODO: counter, up-down counter, gauge, histogram; synchronous vs asynchronous (observable) instruments

### 2. Aggregation and temporality

- TODO: sum/last-value/histogram aggregations; cumulative vs delta temporality and why it matters for the backend

### 3. Exemplars

- TODO: attach trace context to data points to pivot from a metric to a trace

### 4. Practical rule

```text
Pick the instrument that matches the measurement; keep label cardinality low.
Use histograms for latency; attach exemplars to jump to traces.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: follow metric semantic conventions; bound label cardinality; prefer histograms for latency

### Operations and production

- TODO: match temporality to the backend (delta vs cumulative); enable exemplars where supported

## References

- Official docs: https://opentelemetry.io/docs/concepts/signals/metrics/
- Related: [signals.md](signals.md), [signal-traces.md](signal-traces.md), [concept-semantic-conventions.md](concept-semantic-conventions.md)
- Overview: [fundamentals.md](fundamentals.md)
