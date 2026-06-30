# OpenTelemetry — instrumentation libraries

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. What they wrap](#1-what-they-wrap)
  * [2. How you add them](#2-how-you-add-them)
  * [3. Native instrumentation](#3-native-instrumentation)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Instrumentation libraries are prebuilt packages that generate telemetry from the popular frameworks your application already uses, so you do not have to write span or metric code by hand. Each one targets a specific library and knows how to observe the work that library does. They are the components that make automatic instrumentation possible.

What they wrap is the set of boundaries where your application talks to the outside world. There are instrumentation libraries for web servers and HTTP clients, for remote procedure call frameworks, for database drivers, for message queues, and for caches. Wherever a request enters, a query goes out, or a message is published, a matching library can be there to record it.

The telemetry they produce is not generic. Because they are written against the semantic conventions, the spans and metrics they emit use the agreed attribute names, so an HTTP span from one library looks like an HTTP span from another. That consistency is what lets dashboards and queries work across services without custom mapping.

You bring them in either explicitly or automatically. In the explicit style you add the library as a dependency and register it in your startup code, which gives you fine control. In the zero-code style an agent discovers and loads the right libraries for you at launch, with no source changes at all.

The reason they are so valuable is that the most useful telemetry usually lives at the boundaries your code crosses rather than deep inside your own functions, and those boundaries are exactly what shared frameworks own. Increasingly, libraries are even shipping this instrumentation built in, removing the need for a separate wrapper. Either way, they give you broad coverage cheaply, leaving manual instrumentation for the handful of domain spans only your code can describe.

---

## Detailed explanation with examples

### 1. What they wrap

- TODO: HTTP servers/clients, gRPC, DB drivers, message queues, caches

### 2. How you add them

- TODO: explicit dependency + register; vs zero-code agents that load them automatically

### 3. Native instrumentation

- TODO: libraries increasingly ship OTel calls built in, removing the need for a wrapper

### 4. Practical rule

```text
Add the instrumentation library for every framework on a request path.
Auto-instrument the boundaries; hand-write only the domain spans.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: enable libraries for all I/O boundaries; verify they emit semantic-convention attributes

### Operations and production

- TODO: track library versions vs SDK; watch for double-instrumentation when a lib goes native

## References

- Official docs: https://opentelemetry.io/docs/concepts/instrumentation/libraries/
- Components overview: https://opentelemetry.io/docs/concepts/components/
- Related: [component-instrumentation-and-sdks.md](component-instrumentation-and-sdks.md), [component-zero-code-instrumentation.md](component-zero-code-instrumentation.md)
- Overview: [fundamentals.md](fundamentals.md)
