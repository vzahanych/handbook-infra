# Dash0 OpenTelemetry-native — fundamentals

## Core idea

Being OpenTelemetry-native is Dash0's defining architectural choice: it ingests OTLP directly, with no proprietary agent and no closed wire format between your services and the backend. You point existing OTel SDKs or a Collector at Dash0's OTLP endpoint and all three signals arrive in their standard shape, keyed by OpenTelemetry semantic conventions. The same standards-first stance runs through the whole platform — PromQL for queries, Perses for dashboards — so telemetry and skills stay portable instead of locked in.

---

## Cards in this folder

- [otlp-ingest.md](otlp-ingest.md) — sending OTLP straight to Dash0 from SDKs or a Collector.
- [no-agent-no-lock-in.md](no-agent-no-lock-in.md) — why dropping the proprietary agent removes lock-in.
- [collector-and-sdks.md](collector-and-sdks.md) — where SDKs end and the Collector begins.
- [semantic-conventions.md](semantic-conventions.md) — standard attribute names that keep data queryable.

---

## References

- Official site: https://www.dash0.com
- Related: [../../opentelemetry/fundamentals.md](../../opentelemetry/fundamentals.md)
