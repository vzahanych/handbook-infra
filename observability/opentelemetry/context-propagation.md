# OpenTelemetry — context propagation

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Inject and extract](#1-inject-and-extract)
  * [2. W3C Trace Context](#2-w3c-trace-context)
  * [3. Propagating through everything](#3-propagating-through-everything)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Context propagation is what links telemetry across service boundaries, and it is central to distributed tracing working at all. When a service calls another, the current trace context — trace ID, span ID, and flags — is injected into the request, usually as W3C Trace Context headers, and extracted on the other side so the new spans attach to the same trace.

OTel standardizes the propagation format so services in different languages interoperate. Without correct propagation, traces fragment into disconnected pieces, so ensuring it flows through every hop, including gateways and message queues, is essential.

---

## Detailed explanation with examples

### 1. Inject and extract

- TODO: inject context outbound, extract inbound

### 2. W3C Trace Context

- TODO: `traceparent`/`tracestate` headers; baggage

### 3. Propagating through everything

- TODO: gateways, async/queues, batch jobs

### 4. Practical rule

```text
Propagate W3C Trace Context on every hop, including queues and gateways.
Broken propagation fragments traces.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: standardize on W3C tracecontext; carry context across async boundaries

### Operations and production

- TODO: test end-to-end propagation; fix hops that drop context

## References

- Official docs: https://opentelemetry.io/docs/concepts/context-propagation/
- Overview: [fundamentals.md](fundamentals.md)
