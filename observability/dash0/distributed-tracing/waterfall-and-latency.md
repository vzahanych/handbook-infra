# Dash0 distributed tracing — waterfall and latency

## Core idea

The trace waterfall lays spans out on a timeline so the critical path and the slow segment are visible at a glance. Reading where time actually goes — a downstream call, a database query, a queue wait — is how you locate latency instead of guessing. The waterfall turns "the request is slow" into "this span took 80% of the time," which is the precise statement an engineer can act on.

---

## References

- Official site: https://www.dash0.com
- Related: [../application-performance-monitoring/bottleneck-analysis.md](../application-performance-monitoring/bottleneck-analysis.md)
