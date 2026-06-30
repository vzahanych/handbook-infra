# Dash0 log management — OTLP log ingest

## Core idea

Logs enter Dash0 as a first-class OpenTelemetry signal over OTLP, carrying the same resource attributes as the traces and metrics from the same service. Treating logs as structured OTel records — not opaque text lines — is what makes them joinable to the rest of the telemetry by service, pod, or trace id. The ingest path is the foundation that the search and correlation features build on.

---

## References

- Official site: https://www.dash0.com
- Related: [../../opentelemetry/signals.md](../../opentelemetry/signals.md)
