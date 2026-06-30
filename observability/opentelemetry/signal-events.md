# OpenTelemetry — events

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. A named, structured log](#1-a-named-structured-log)
  * [2. Events versus span events](#2-events-versus-span-events)
  * [3. Status and stability](#3-status-and-stability)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

An event is a specialized kind of log that captures a discrete, well-defined occurrence. Where an ordinary log is often a free-form message, an event is meant to be a recognizable thing that happened, with a name and a predictable shape. It is a signal still under development, growing out of the logs work rather than standing entirely on its own.

Concretely, an event is built on the log data model but adds the discipline of a name and a structured body. The name identifies the type of occurrence, such as a user signing in or a button being clicked, and the body carries the fields that always accompany that type. Because the shape is consistent, tools can reason about events of the same name as a population rather than parsing each message individually.

This is where events differ from the older idea of span events. A span event is a marked moment recorded inside a particular span, tied to that span's lifetime, whereas an event in this newer sense is a standalone record in the log stream, correlated with traces through context but not embedded in a span. The direction of travel is toward expressing these occurrences as first-class events rather than notes attached to spans.

A natural way to picture them is as the structured cousins of analytics or domain events. The same things a product team might track, like a feature being used or a checkout completing, can be emitted as OpenTelemetry events and flow through the same pipeline as the rest of your telemetry. That lets behavioral data and operational data share one path and one context.

Because the signal is still being specified, the practical stance is to treat it as emerging. The concepts and the data model exist and are worth understanding, but the application programming interfaces and conventions are still settling, so you should expect change before relying on events as a stable production foundation.

---

## Detailed explanation with examples

### 1. A named, structured log

- TODO: event name + structured body atop the log data model; consistent shape per name

### 2. Events versus span events

- TODO: standalone log-stream events vs span events bound to a span's lifetime

### 3. Status and stability

- TODO: in-development signal; APIs/conventions still evolving

### 4. Practical rule

```text
Model discrete occurrences as named events with a consistent body.
Treat the signal as emerging — expect the API and conventions to change.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: give events stable names and structured fields; correlate via context

### Operations and production

- TODO: track spec maturity before depending on events; route them through the log pipeline

## References

- Official docs: https://opentelemetry.io/docs/concepts/signals/
- Related: [signal-logs.md](signal-logs.md), [signals.md](signals.md)
- Overview: [fundamentals.md](fundamentals.md)
