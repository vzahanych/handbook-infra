# OpenTelemetry — baggage

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. How baggage travels](#1-how-baggage-travels)
  * [2. Baggage versus span attributes](#2-baggage-versus-span-attributes)
  * [3. Cautions](#3-cautions)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Baggage is contextual information that rides along with a request as it travels through your system. It is a small set of key and value pairs that you set early, perhaps at the edge where a request first arrives, and that any later service can read without having to look the value up again. Think of it as a note pinned to the request that everyone downstream can see.

The way baggage moves is the same way trace context moves: it is propagated from one service to the next, usually in a request header. When a service makes an outbound call, the current baggage is injected alongside the trace context, and the receiving service extracts it and carries it onward. Because it follows the same path, baggage reaches every hop that propagation reaches.

It helps to be clear about what baggage is not. Baggage is not automatically added to your spans, metrics, or logs; it is simply made available, and it is up to you to decide whether to copy a particular value onto a span as an attribute. This separation is deliberate, because it lets you carry a value for use later without paying to store it on every span in between.

A typical use is propagating a fact that is known only at the start but useful much later. The classic example is a tenant or account identifier, established when the request enters and then read deep in a backend service so it can be attached to the spans that matter there. Without baggage, that downstream service would have no way to know which tenant the request belonged to.

Because baggage is broadcast to everything downstream, it comes with cautions. It travels in headers, so keeping it small matters for performance, and it may cross trust boundaries, so it should never carry secrets or sensitive personal data. Used with that restraint, baggage is a clean way to move a little shared context exactly where it is needed.

---

## Detailed explanation with examples

### 1. How baggage travels

- TODO: W3C Baggage header; injected/extracted with context on every hop

### 2. Baggage versus span attributes

- TODO: baggage is available, not auto-recorded; copy onto spans deliberately

### 3. Cautions

- TODO: header size limits; never carry secrets/PII; crosses service/trust boundaries

### 4. Practical rule

```text
Use baggage to carry a small key set context downstream (e.g. tenant ID).
Copy onto spans only when needed; never put secrets in baggage.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: set baggage at the edge; configure the baggage propagator; copy chosen keys onto spans

### Operations and production

- TODO: keep baggage small; strip it at trust boundaries; never include sensitive data

## References

- Official docs: https://opentelemetry.io/docs/concepts/signals/baggage/
- Related: [component-context-propagation.md](component-context-propagation.md), [signals.md](signals.md)
- Overview: [fundamentals.md](fundamentals.md)
