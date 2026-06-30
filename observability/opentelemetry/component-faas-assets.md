# OpenTelemetry — Function-as-a-Service assets

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Instrumentation layers](#1-instrumentation-layers)
  * [2. Collector layer](#2-collector-layer)
  * [3. Cold starts and flushing](#3-cold-starts-and-flushing)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Function-as-a-Service assets are prebuilt packages that bring OpenTelemetry to serverless functions, where the usual ways of running an agent simply do not apply. In practice they are mostly delivered as layers for AWS Lambda, a layer being a bundle of code you attach to a function without baking it into your own deployment. They exist to make instrumenting a function a matter of attaching something and setting a few variables, rather than reworking the function itself.

They come in two kinds, and the first is the instrumentation layer. This bundles the interface, the kit, and a set of automatic instrumentation libraries, and wires them into the function so it starts emitting traces and metrics for the events and calls it handles. It is the serverless equivalent of zero-code instrumentation, packaged for a place where you cannot install an agent on a host.

The second kind is the collector layer. Because there is no long-lived machine nearby to send data to, this layer runs a small collector inside the function's own execution environment as an extension. The function exports its telemetry locally to that collector, and the collector takes responsibility for forwarding it onward, which keeps the export fast and off the request's critical path.

The serverless lifecycle is what makes all this necessary. Invocations are short, there is no host you control, and the runtime may freeze the moment a request finishes and thaw again for the next one. The assets handle that lifecycle, and in particular they make sure pending telemetry is flushed before the environment freezes, so that data is not silently lost between invocations.

For the same reason, cold starts are the cost to watch. Loading the layers adds time to the first invocation after a function scales up, so the practical advice is to keep batching small and timeouts short, and to confirm that telemetry flushes on shutdown. With those settings in place, a function gains full observability simply by attaching the layers and configuring them through environment variables.

---

## Detailed explanation with examples

### 1. Instrumentation layers

- TODO: language-specific Lambda layers adding SDK + auto-instrumentation via env vars

### 2. Collector layer

- TODO: Collector as a Lambda extension; function exports to localhost, layer forwards on

### 3. Cold starts and flushing

- TODO: cold-start overhead; flush spans before freeze; short timeouts/batching

### 4. Practical rule

```text
Attach the instrumentation layer + Collector extension; configure via env vars.
Flush before the runtime freezes so no spans are lost.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: add the layer, set OTEL_ env vars, export to the in-process Collector extension

### Operations and production

- TODO: budget cold-start cost; ensure flush-on-shutdown; keep batch/timeout small

## References

- Official docs: https://opentelemetry.io/docs/platforms/faas/
- Components overview: https://opentelemetry.io/docs/concepts/components/
- Related: [component-collector.md](component-collector.md), [component-zero-code-instrumentation.md](component-zero-code-instrumentation.md)
- Overview: [fundamentals.md](fundamentals.md)
