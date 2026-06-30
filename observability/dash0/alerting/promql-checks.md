# Dash0 alerting — PromQL checks

## Core idea

Checks are defined in real PromQL — the actual Prometheus query language — over metrics, and via the query builder over logs and traces as well. Supporting genuine PromQL rather than a near-clone means existing Prometheus alerting rules port directly and engineers reuse a skill they already have. A check is just a query plus a threshold and a duration, which keeps alert definitions declarative and portable.

---

## References

- Official site: https://www.dash0.com
- Related: [../../prometheus/fundamentals.md](../../prometheus/fundamentals.md)
