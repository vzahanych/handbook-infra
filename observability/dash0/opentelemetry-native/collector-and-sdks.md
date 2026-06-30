# Dash0 OpenTelemetry-native — Collector and SDKs

## Core idea

Telemetry reaches Dash0 either straight from OpenTelemetry SDKs in the application or via an OpenTelemetry Collector that sits in between. SDKs produce the signals and propagate context; the Collector is the optional aggregation point where you centralize batching, sampling, enrichment, and routing before export. Choosing one or both is a deployment decision — direct SDK export is simplest, while a Collector gives you a single control point for processing across many services.

---

## References

- Official site: https://www.dash0.com
- Related: [../../opentelemetry/component-collector.md](../../opentelemetry/component-collector.md), [../../opentelemetry/component-instrumentation-and-sdks.md](../../opentelemetry/component-instrumentation-and-sdks.md)
