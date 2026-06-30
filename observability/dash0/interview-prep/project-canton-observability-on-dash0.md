# Project — Canton Network observability, migrated from Grafana to Dash0

> **Dimension:** OpenTelemetry-native platform integration on a real, runnable
> system — not a scaffold. The Canton Network App Quickstart ships a working
> Grafana/LGTM observability module; this project re-points it at Dash0 by
> changing the OpenTelemetry Collector's exporters, and keeps the Canton-specific
> data-plane logic. Every claim here is demonstrable on `cn-quickstart`, so you
> can speak to it without inventing numbers. Where you have run it yourself,
> replace the `[bracketed]` figures with what you actually observed.

---

## The 30-second version (lead with this)

> "Canton — the network big institutions are building on — already ships an
> OpenTelemetry-native observability stack: an OTel Collector fanning traces,
> metrics, and logs into Tempo, Prometheus, and Loki, visualized in Grafana. The
> interesting thing is that the Collector is the only part doing Canton-specific
> work; the four backends behind it are generic, stateful infrastructure you have
> to operate. Because Canton is OTLP-native end to end, migrating the whole thing
> to Dash0 is a change to the Collector's *exporters* — three become one — and
> you delete Prometheus, Loki, Tempo, and Grafana. The point I'd make in the
> interview is that this is Dash0's pitch made literal: same signals, same
> transaction-level traces, one OTLP backend instead of a four-service stack to
> run, and it's reversible because nothing got re-instrumented."

Then walk the layers below as they dig.

---

## Context

Canton Network is a privacy-enabled blockchain that financial institutions are
adopting for tokenized assets and settlement, and its App Developer Quickstart
(`cn-quickstart`) is the reference deployment a team starts from. That quickstart
includes an optional **observability module** —
`quickstart/docker/modules/observability/`, switched on with the `observability`
Docker Compose profile during `make setup` — so observability here is not a
greenfield design but an existing, opinionated stack I'm migrating. That matters
for the story: the credibility comes from working *with* a real system's
telemetry rather than narrating a hypothetical one.

The stack Canton ships is the standard "LGTM" arrangement. An **OpenTelemetry
Collector** (`otel/opentelemetry-collector-contrib:0.108.0`) is the hub; behind
it sit **Prometheus** for metrics, **Loki** for logs, **Tempo** for traces, and
**Grafana** for visualization, plus cAdvisor, the Postgres exporter, and the
Nginx exporter feeding host- and dependency-level metrics. It monitors the
components that make Canton *Canton*: participant nodes, the sequencer and
synchronization-domain components, the backend application service, the
Participant Query Store (PQS), and the Nginx reverse proxy.

## The problem / constraint

The observable unit in Canton is a **transaction**, and tracing one end to end is
the whole reason the stack exists. A single ledger transaction flows across
several processes — the backend's POST handler, a PQS query, a call to the
App-Provider Ledger API, then the participant node preparing the transaction and
submitting it onto the network through the sequencer — and the value of the
observability stack is being able to follow that one transaction across all of
them. Canton makes this possible by honoring OpenTelemetry `TraceId`/`SpanId`
throughout its gRPC/HTTP interfaces and by carrying a dense set of correlation
identifiers — `WorkflowId`, `CommandId`, `SubmissionId`, `TransactionId`,
`LedgerEventId`, `LedgerOffset`, `ContractId`, `TemplateId`, `PartyId`.

The cost of that capability is **operational weight**, and that is the constraint
the migration targets. Of the six-plus services in the module, exactly one — the
Collector — does anything Canton-aware; the other backends are generic stateful
systems that someone has to run, scale, retain data in, and secure. So the
problem is not "can we observe Canton" (the quickstart already does) but "can we
keep the transaction-level observability while removing the four-service stack a
team would otherwise operate" — which is precisely the question Dash0 exists to
answer.

## My role and the key decisions

I treated this as a Collector-pipeline migration, because that is where all the
leverage and all the Canton-specific logic live. The decisions, each as a
trade-off rather than a fact:

- **Collapse three exporters into one OTLP exporter; keep the receivers and
  processors.** Canton's `collector.yaml` defines three egress exporters —
  `otlphttp/prometheus`, `otlphttp/loki`, and `otlp/tempo` — wired through four
  pipelines (`metrics`, `traces`, `logs/1` from OTLP, `logs/2` from
  fluentforward). The migration replaces all three with a single `otlphttp/dash0`
  exporter (Dash0 OTLP endpoint plus an `Authorization: Bearer` token and a
  dataset header) and points every pipeline at it. The receivers (OTLP gRPC,
  Prometheus scrape of `canton`/`splice`/cadvisor/nginx/postgres, fluentforward)
  do not change. The trade-off I can defend: one backend means one less
  *correlation* problem too — traces, metrics, and logs now share a single store
  instead of being stitched together across three.
- **Preserve the Canton-specific transform processors — that's the real
  engineering.** The config's value is not the exporters but two
  `transform/...` processors: one parses Canton's JSON log bodies, extracts
  `trace-id`, fixes the timestamp, and unpacks the logger name into a clean
  `service.name`; another promotes container names to service names for
  fluentd-sourced logs. This is OTel Collector OTTL work, it is backend-agnostic,
  and it survives the migration unchanged. Keeping it is the point: **the
  Collector is portable; the backend is a choice.**
- **Delete the four backend services rather than re-point them.** Prometheus,
  Loki, Tempo, and Grafana (and their volumes, retention config, and Grafana
  provisioning) come out of the compose profile entirely. The trade-off is
  explicit: I give up self-hosted, on-prem storage of telemetry in exchange for
  not operating four stateful systems — and for an institution-facing network
  that data-residency question is the honest counter-argument I have to address,
  not hide (see *What I'd do differently*).
- **Dashboards as code via Perses; alerting via PromQL.** Canton ships Grafana
  dashboards (`Infrastructure`, `Participant`, `Platform`, and a consolidated-logs
  view). Their Dash0 equivalents are Perses dashboards kept in Git as
  observability-as-code, and the alerting that Grafana would carry becomes PromQL
  checks. The trade-off: re-authoring dashboards is real work, but Perses is an
  open schema, so this is portability rather than re-platforming onto another
  proprietary format.
- **Treat reversibility as a feature, not an afterthought.** Because every hop is
  OTLP and nothing in Canton was re-instrumented, flipping the exporter block back
  restores the Grafana stack. I'd keep the migration as a Collector config
  variant so the choice of backend stays a one-file decision — which is the
  cleanest possible demonstration of "no lock-in."

## Impact

The honest framing: this is an **integration and operational-surface** result,
not a latency micro-benchmark. State it that way.

- **Backend services to operate: four → zero** (Prometheus, Loki, Tempo,
  Grafana removed); the only telemetry component left in the team's compose is the
  Collector they already ran.
- **Exporters: three → one**; the three-way trace↔metric↔log correlation that
  Grafana wires up with derived fields becomes intrinsic, because all three
  signals land in one store.
- **Transaction-level observability preserved**: a transaction is still
  followable from the backend POST through PQS, the Ledger API, and the
  participant node's submission, via the same `TraceId` Canton already
  propagates — now without the manual log→Tempo→log hop-stitching.
- **Reversible migration**: re-instrumentation required to switch backends = none;
  the change is localized to the Collector's exporter block.
- `[If you ran it: time-to-first-trace in Dash0, container/RAM footprint dropped
  by removing the four backends, or setup steps eliminated — quote one real
  number you measured.]`

> If you have run `cn-quickstart` and pointed it at Dash0, lead with the one real
> observation you made (e.g. "the same transaction trace showed up in Dash0 with
> no code change"). If you have only read the configs, say so and lead with the
> exporter-collapse and service-count facts, which are verifiable from the repo.

## What I'd do differently

I'd design the **data-egress and redaction story before the migration, not
after**, because Canton is bank-facing and its correlation identifiers
(`PartyId`, `ContractId`) can be sensitive. Self-hosting the LGTM stack keeps all
telemetry on-prem by default; moving to a SaaS backend means I owe an explicit
answer on data residency and on redacting or dropping sensitive attributes at the
Collector edge (an OTTL processor) before anything leaves the boundary. I'd also
**quantify the operational savings up front** — RAM, container count, retention
storage removed — so the "easier than Grafana" claim is a measured number rather
than an assertion, and I'd build the Perses dashboards in parallel with the cutover
so there's never a visualization gap.

---

## Likely follow-up questions (and how to handle them)

- **"What in the Collector config actually changes?"** Only the `exporters`
  block and the `exporters:` list in each pipeline. Three exporters
  (`otlphttp/prometheus`, `otlphttp/loki`, `otlp/tempo`) become one
  `otlphttp/dash0` with the Dash0 endpoint and auth header; receivers and the
  `transform` processors are untouched. That specificity is the senior signal.
- **"How is a Canton transaction traced end to end?"** Canton honors
  `TraceId`/`SpanId` across its gRPC/HTTP interfaces, so one transaction's spans
  span the backend handler → PQS → Ledger API → participant node → sequencer. In
  the Grafana stack you pivot log→Tempo→log via derived fields; in Dash0 the
  three signals are one store, so the correlation is built in.
- **"What do you lose by dropping the self-hosted stack?"** On-prem data
  residency and full control of retention. For a regulated, institution-facing
  network that's the real trade-off — answer it with edge redaction and a
  residency check, don't wave it away.
- **"Why is this reversible / why no lock-in?"** Nothing in Canton was
  re-instrumented; it emits OTLP either way. The backend is selected by the
  Collector's exporter block, so reverting is a one-file change. That's the
  literal demonstration of Dash0's "OTLP-native, no agent, no lock-in" claim.
- **"Where's the cost risk?"** Canton metrics are high-cardinality (per-party,
  per-domain, per-contract). Under Dash0's volume-based pricing that cardinality
  is a cost lever, so I'd add cardinality limits / sampling at the Collector — the
  same control that's good reliability hygiene anyway.
- **"Why should Dash0 care about Canton?"** It's an OTLP-native, fast-growing,
  institution-backed network whose reference stack is *already* the Grafana
  competitor Dash0 displaces — a warm, technically-clean migration path into
  exactly Dash0's target accounts.

## The Dash0 connection (steer here on purpose)

This project *is* Dash0's thesis, demonstrated on a system their target customers
are adopting: **OTLP-native ingest** ([../opentelemetry-native/otlp-ingest.md](../opentelemetry-native/otlp-ingest.md)),
**no agent / no lock-in** ([../opentelemetry-native/no-agent-no-lock-in.md](../opentelemetry-native/no-agent-no-lock-in.md))
made literal by a reversible one-file cutover, **one store for three signals** so
the trace↔log↔metric correlation Grafana stitches by hand comes for free, and
**Perses dashboards-as-code** ([../dashboards/perses.md](../dashboards/perses.md))
replacing Grafana provisioning. The pivot to make in the call: *"the four backends
behind Canton's Collector are exactly what Dash0 replaces — and because Canton is
OTLP-native, that's a config change, not a re-platforming. Where do you see the
data-residency objection landing for the bank-facing customers, and is edge
redaction in the Collector the answer you'd give them?"* That puts you inside their
go-to-market, not just their product.

When the conversation reaches root cause, hand it to **Agent0**
([../agent0/root-cause-and-code.md](../agent0/root-cause-and-code.md)): the manual
"find the trace, follow it across participant and sequencer, read the waterfall"
work is precisely what Agent0 automates over the same OTLP data.

---

## Reproduce it (so the story is real, not narrated)

- Canton observability overview:
  https://docs.digitalasset.com/build/3.5/quickstart/observe/observability-troubleshooting-overview.html
- Canton observability module (real configs):
  `digital-asset/cn-quickstart` → `quickstart/docker/modules/observability/`
  (`compose.yaml`, `compose.env`, and
  `conf/{otel-collector,prometheus,loki,tempo,grafana}/`).
- The file that does all the work: `conf/otel-collector/collector.yaml` — the
  receivers, the two Canton `transform` processors, and the three exporters you
  collapse into one.
- To run: enable the `observability` profile in `make setup`, bring the stack up,
  exercise a transaction, then change `collector.yaml`'s exporters to a single
  `otlphttp/dash0` and confirm the same transaction trace appears in Dash0.

See: [../opentelemetry-native/collector-and-sdks.md](../opentelemetry-native/collector-and-sdks.md),
[../observability-as-code/gitops-workflow.md](../observability-as-code/gitops-workflow.md),
[../distributed-tracing/spans-and-context.md](../distributed-tracing/spans-and-context.md).
