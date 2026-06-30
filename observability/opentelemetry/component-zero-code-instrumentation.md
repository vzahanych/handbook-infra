# OpenTelemetry — zero-code instrumentation

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. How it attaches](#1-how-it-attaches)
  * [2. What you get and what you don't](#2-what-you-get-and-what-you-dont)
  * [3. Configuration](#3-configuration)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Zero-code instrumentation adds telemetry to an application without touching its source code. It bundles the interface, the kit, and a set of instrumentation libraries, and attaches them from the outside, so an unmodified program begins emitting traces, metrics, and logs the moment it starts. It is the quickest route to observability, especially for software you cannot easily change or rebuild.

How it attaches depends on the language. In some runtimes a separate agent loads alongside the program and rewrites the relevant code in memory as it runs. In others a launcher wraps the start command and pulls in the instrumentation, or a module loads automatically before your code does. In every case the goal is the same: the framework calls get observed without anyone editing them.

You steer it through environment variables rather than code. A few settings name the service, point the exporter at a collector, choose how aggressively to sample, and select which propagation format to use. Because the configuration lives outside the program, the same image can be tuned differently in development and in production.

What you get is broad coverage of the boundaries the bundled libraries understand, which is to say the same incoming and outgoing calls that instrumentation libraries observe. What you do not get is insight into your own business logic, since an external agent has no way to know which internal operations are meaningful to your domain.

That gap is why zero-code instrumentation is best seen as a foundation rather than a finish line. You attach it for instant breadth, then layer a small amount of manual instrumentation on top for the operations that matter most. The two approaches share the same kit underneath, so they combine cleanly into one coherent set of telemetry.

---

## Detailed explanation with examples

### 1. How it attaches

- TODO: Java javaagent, Python `opentelemetry-instrument`, .NET/Node auto-loaders, eBPF approaches

### 2. What you get and what you don't

- TODO: framework spans/metrics for free; domain spans still need manual code

### 3. Configuration

- TODO: `OTEL_*` env vars — service.name, exporter endpoint, sampler, propagators

### 4. Practical rule

```text
Attach zero-code for instant breadth; configure via OTEL_ env vars.
Layer manual spans on top for the logic the agent can't see.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: set OTEL_SERVICE_NAME and resource attrs; point the exporter at a Collector

### Operations and production

- TODO: measure agent overhead; pin versions; avoid mixing zero-code with conflicting manual setup

## References

- Official docs: https://opentelemetry.io/docs/concepts/instrumentation/zero-code/
- Components overview: https://opentelemetry.io/docs/concepts/components/
- Related: [component-instrumentation-libraries.md](component-instrumentation-libraries.md), [component-instrumentation-and-sdks.md](component-instrumentation-and-sdks.md)
- Overview: [fundamentals.md](fundamentals.md)
