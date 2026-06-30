# Dash0 log management — fundamentals

## Core idea

Log management ingests logs over OTLP and makes them searchable and filterable with instant access to the context around each line. Because logs land in the same store as traces and metrics and carry OpenTelemetry resource attributes, a log can be pivoted directly to the trace, service, or pod that produced it — collapsing the usual cross-tool hunt into one view. The emphasis is on fast, contextual exploration rather than logs as an isolated silo.

---

## Cards in this folder

- [otlp-log-ingest.md](otlp-log-ingest.md) — logs as a first-class OTel signal.
- [search-and-filter.md](search-and-filter.md) — exploring logs quickly.
- [context-and-correlation.md](context-and-correlation.md) — pivoting from a log to its trace and resource.

---

## References

- Official site: https://www.dash0.com
- Related: [../distributed-tracing/fundamentals.md](../distributed-tracing/fundamentals.md), [../../loki/fundamentals.md](../../loki/fundamentals.md)
