# OpenTelemetry — traces

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Spans](#1-spans)
  * [2. The span tree](#2-the-span-tree)
  * [3. What a span carries](#3-what-a-span-carries)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

A trace is the story of a single request as it moves through your system. From the moment a request arrives to the moment a response goes back, the trace records every meaningful step along the way, even when those steps happen in different services on different machines. It is the signal that answers the question "what actually happened to this one request, and where did the time go?"

The building block of a trace is the span. A span represents one unit of work, such as handling an incoming call, running a database query, or making an outbound request, and it carries a start time and a duration. Each span also has its own identifier and the identifier of the trace it belongs to, which is how individual pieces of work are recognized as part of the same request.

Spans are not a flat list; they form a tree. The first span, called the root, represents the overall request, and every span it triggers becomes a child, which in turn may have children of its own. This parent and child structure is what lets you see that the slow database query lived inside the checkout step, which lived inside the original web request.

Beyond timing, a span carries detail that explains it. It holds attributes, which are key and value pairs describing the work, such as the HTTP route or the database statement; it can hold span events, which mark notable moments within the span; and it has a status that records whether the work succeeded or failed. Together these turn a bare duration into something you can actually diagnose.

What makes traces powerful is that they cross service boundaries, which only works because the trace context is propagated from one hop to the next. When propagation is intact, a single trace can span a browser, a gateway, and a dozen backend services, and you can follow one request end to end. When it breaks, the trace fragments, which is why carrying context everywhere is the discipline that keeps tracing useful.

---

## Detailed explanation with examples

### 1. Spans

- TODO: start/end, duration, span context (trace ID, span ID, flags); kinds (server, client, internal, producer, consumer)

### 2. The span tree

- TODO: root vs child spans, parent links, span links across traces

### 3. What a span carries

- TODO: attributes, span events, status, exceptions recorded as events

### 4. Practical rule

```text
Model one unit of work per span; name spans by operation, not by data.
Set status on failure and propagate context so the tree stays whole.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: use semantic-convention attributes; record exceptions; keep span names low-cardinality

### Operations and production

- TODO: sample to control volume but always keep errors and slow traces; watch span/attribute cardinality

## References

- Official docs: https://opentelemetry.io/docs/concepts/signals/traces/
- Related: [signals.md](signals.md), [component-context-propagation.md](component-context-propagation.md), [component-samplers.md](component-samplers.md)
- Overview: [fundamentals.md](fundamentals.md)
