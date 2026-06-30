# Dash0 — fundamentals

## Core idea

Dash0 is an OpenTelemetry-native observability platform that unifies metrics, logs, and traces in a single backend, so you instrument once with OTel and send the data straight to Dash0 over OTLP without a proprietary agent. Because it speaks the open standard end to end — OTLP for ingest, PromQL for queries, Perses for dashboards, and OpenTelemetry semantic conventions for naming — it avoids the vendor lock-in of agent-based suites while still offering the full breadth of an APM tool. Its pitch is full-stack observability that is open by default, predictable in cost, and increasingly automated by an AI agent (Agent0) that investigates incidents and proposes fixes.

The platform is organized as a set of products built on that shared OTel foundation. Ingestion and instrumentation (OpenTelemetry-native, integrations, language and cloud monitoring) feed the data plane; the analysis products (infrastructure, Kubernetes, logs, tracing, APM, frontend, synthetic) read it; and the workflow layer (dashboards, alerting, service map, observability-as-code, Agent0) turns it into action. The cost model is deliberately transparent — priced on telemetry volume — which is a core part of the product positioning.

---

## Products in this folder

Each product has its own folder with a `fundamentals.md` hub and deep-dive cards. This file is the map.

### Foundation

- [opentelemetry-native](opentelemetry-native/fundamentals.md) — OTLP-native ingest, no proprietary agent, no lock-in.
- [integrations](integrations/fundamentals.md) — pre-built connectors plus Node.js, Java, Python, and Google Cloud monitoring.

### Analysis products

- [infrastructure-monitoring](infrastructure-monitoring/fundamentals.md) — health and performance of hosts and infra components.
- [kubernetes-monitoring](kubernetes-monitoring/fundamentals.md) — dedicated observability for containerized environments.
- [log-management](log-management/fundamentals.md) — search, filter, and correlate logs with context.
- [distributed-tracing](distributed-tracing/fundamentals.md) — request flows across services to find errors and latency.
- [application-performance-monitoring](application-performance-monitoring/fundamentals.md) — application behavior and bottlenecks.
- [real-user-monitoring](real-user-monitoring/fundamentals.md) — frontend and user-experience metrics (website monitoring).
- [synthetic-monitoring](synthetic-monitoring/fundamentals.md) — proactive testing of endpoints and user journeys.

### Workflow and automation

- [dashboards](dashboards/fundamentals.md) — Perses-based, import/export-portable dashboards.
- [alerting](alerting/fundamentals.md) — PromQL checks and 400+ pre-built alert templates.
- [service-map](service-map/fundamentals.md) — visual service dependencies and interactions.
- [observability-as-code](observability-as-code/fundamentals.md) — dashboards and alerts managed via Git and APIs.
- [agent0](agent0/fundamentals.md) — autonomous AI engineer that investigates incidents and opens PRs.
- [pricing-and-cost](pricing-and-cost/fundamentals.md) — transparent, volume-based pricing model.

---

## References

- Official site: https://www.dash0.com
- Related: [../opentelemetry/fundamentals.md](../opentelemetry/fundamentals.md), [../prometheus/fundamentals.md](../prometheus/fundamentals.md), [../grafana/fundamentals.md](../grafana/fundamentals.md)
