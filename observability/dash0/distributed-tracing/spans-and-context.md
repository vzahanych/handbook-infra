# Dash0 distributed tracing — spans and context

## Core idea

A trace is assembled from spans — timed units of work — linked by trace and span ids that propagate across service boundaries via W3C Trace Context. Each hop continues the same trace by carrying that context in its headers, so independent services produce spans that Dash0 can stitch into one request. Correct context propagation is the precondition for everything else: without it traces fragment and the cross-service picture breaks.

---

## References

- Official site: https://www.dash0.com
- Related: [../../opentelemetry/component-context-propagation.md](../../opentelemetry/component-context-propagation.md)
