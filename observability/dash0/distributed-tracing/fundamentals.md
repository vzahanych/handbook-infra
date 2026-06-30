# Dash0 distributed tracing — fundamentals

## Core idea

Distributed tracing visualizes the path of a request as it flows across services, so you can see where errors originate and where latency accumulates. It consumes standard OpenTelemetry spans propagated with W3C Trace Context, reconstructs them into end-to-end traces, and surfaces the slow or failing span in a waterfall. Because spans share the store with logs and metrics, a trace is the spine that ties the other signals together and feeds both the service map and Agent0's root-cause analysis.

---

## Cards in this folder

- [spans-and-context.md](spans-and-context.md) — spans and how context links them.
- [waterfall-and-latency.md](waterfall-and-latency.md) — reading the trace waterfall for latency.
- [errors-and-root-cause.md](errors-and-root-cause.md) — finding where failures originate.

---

## References

- Official site: https://www.dash0.com
- Related: [../service-map/fundamentals.md](../service-map/fundamentals.md), [../../tempo/fundamentals.md](../../tempo/fundamentals.md)
