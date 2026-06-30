# Dash0 OpenTelemetry-native — OTLP ingest

## Core idea

OTLP ingest is the single front door to Dash0: traces, metrics, and logs all arrive over the OpenTelemetry Protocol, whether emitted directly by an SDK or forwarded by a Collector. Because OTLP is the native format, there is no translation or proprietary re-encoding step — you configure an endpoint and an auth token, and the data lands ready to query. This uniform entry point is what lets the three signals share one store and be correlated downstream.

---

## References

- Official site: https://www.dash0.com
- Related: [../../opentelemetry/component-exporters-and-otlp.md](../../opentelemetry/component-exporters-and-otlp.md)
