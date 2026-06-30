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

Context propagation is the mechanism that links telemetry across service boundaries, and without it distributed tracing simply does not work. The idea is that a small piece of context travels with a request wherever it goes, so that work done in one service can be recognized as part of the same operation in the next. It is the thread that stitches many independent services into a single, coherent trace.

The context being carried is small but precise. It holds the trace identifier that names the overall request, the identifier of the current span that names the immediate parent, and a set of flags, including whether this trace is being sampled. With those few values, a downstream service knows exactly which trace to attach its new spans to.

The movement happens in two steps, called inject and extract. When a service makes an outbound call, the kit injects the context into the request, most often as HTTP headers. When the next service receives that call, it extracts the context from the headers and uses it to continue the trace rather than start a new one.

The format of those headers is standardized so that services written in different languages can understand one another. OpenTelemetry uses the World Wide Web Consortium standard known as Trace Context, which defines two headers, traceparent and tracestate. Alongside the trace context, baggage can travel the same way, carrying small key and value pairs that later services and signals can read.

The hard part in practice is making sure context flows through every single hop. It must survive gateways and proxies, asynchronous boundaries like message queues, and background or batch jobs, because the moment one hop drops it, the trace fragments into disconnected pieces. Treating end-to-end propagation as something to test, not just assume, is what keeps traces whole.

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
