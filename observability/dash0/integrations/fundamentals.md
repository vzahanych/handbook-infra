# Dash0 integrations — fundamentals

## Core idea

Integrations are Dash0's pre-built connectors that get telemetry flowing from a given source with minimal setup, turning a new service or platform observable in minutes instead of after a hand-built pipeline. Because the backend is OTLP-native, most integrations are thin: they configure standard OpenTelemetry instrumentation or a Collector receiver and point it at Dash0 rather than installing a proprietary agent. The catalog spans languages, runtimes, and cloud providers, and everything lands in the same unified store so cross-signal correlation works regardless of origin.

---

## Cards in this folder

- [prebuilt-connectors.md](prebuilt-connectors.md) — the connector catalog and what a connector configures.
- [nodejs-monitoring.md](nodejs-monitoring.md) — tuned OTel instrumentation for Node.js.
- [java-monitoring.md](java-monitoring.md) — JVM-aware instrumentation and views.
- [python-monitoring.md](python-monitoring.md) — observability for Python apps.
- [google-cloud-monitoring.md](google-cloud-monitoring.md) — native GCP resource and log ingest.

---

## References

- Official site: https://www.dash0.com
- Related: [../opentelemetry-native/fundamentals.md](../opentelemetry-native/fundamentals.md)
