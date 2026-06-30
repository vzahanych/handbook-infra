# Dash0 Discovery Call — project walkthrough

This folder holds the project walkthrough to prepare for the Dash0 Discovery Call
(backend / platform). Unlike a generic "tell me about a project" scaffold, this
one is built on a **real, runnable system** — the Canton Network App Quickstart —
so every technical claim is verifiable from public configs rather than mapped onto
bracketed placeholders. Run it, and the walkthrough stops being a narrative and
becomes a demo.

## Why this project

The walkthrough is chosen to sit **directly on Dash0's problem space** rather than
merely adjacent to it, so every decision doubles as a signal that you understand
where Dash0 wins:

- [project-canton-observability-on-dash0.md](project-canton-observability-on-dash0.md)
  — **OTLP-native platform migration**: Canton ships a working Grafana/LGTM
  observability stack (OTel Collector → Prometheus + Loki + Tempo → Grafana) that
  traces ledger transactions end to end. Because Canton is OpenTelemetry-native,
  migrating it to Dash0 is a change to the Collector's *exporters* — three become
  one — and the four backend services come out. It demonstrates Dash0's core
  claims (OTLP-native, no agent, no lock-in, easier than Grafana) on a system
  institutions are actually adopting.

Canton is also the right *business* target to be seen understanding: an
OTLP-native, fast-growing, institution-backed network whose reference stack is
the exact Grafana arrangement Dash0 displaces — a warm, technically-clean
migration path into Dash0's accounts.

## How to deliver the walkthrough (2–3 minutes)

Lead with the shape, not the chronology. The structure the file follows:

1. **Context** — one sentence on the system and why it matters (institutions,
   real money, a shipped reference stack). Enough for the listener to care.
2. **Problem / constraint** — the specific hard thing: keep transaction-level
   observability while removing the four-service backend a team must operate.
3. **Your role and decisions** — what *you* did, the options you weighed, and
   *why*. Trade-offs are where senior signal lives.
4. **Impact** — services removed, exporters collapsed, transaction tracing
   preserved, migration reversible. Quote a real number if you ran it.
5. **What you'd do differently** — the data-residency / redaction story for a
   bank-facing network; shows reflection and honesty.

Then stop and let them dig. The file ends with **likely follow-up questions** and
a **Dash0 connection** paragraph so you can steer toward their domain on purpose.

## Make it real before the call

The strongest version of this walkthrough is one you have actually run. Before the
call: stand up `cn-quickstart` with the `observability` profile, exercise a
transaction in Grafana/Tempo, then re-point the Collector at Dash0 and confirm the
same trace appears. Write down the one true number you observed (time-to-first-
trace, container/RAM footprint removed, setup steps eliminated) and the one
decision you are most ready to defend — the exporter-collapse, or the
data-residency trade-off. If you have only read the configs, say so honestly and
lead with the facts that are verifiable from the repo.

---

## References

- Dash0 product handbook: [../fundamentals.md](../fundamentals.md)
- Canton observability overview:
  https://docs.digitalasset.com/build/3.5/quickstart/observe/observability-troubleshooting-overview.html
- Canton observability module: `digital-asset/cn-quickstart` →
  `quickstart/docker/modules/observability/`
- Code RED podcast (Dash0) and Dash0 docs — listen/skim before the call.
