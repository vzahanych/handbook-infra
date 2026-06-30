# Dash0 website / real-user monitoring — fundamentals

## Core idea

Website monitoring captures frontend and user-experience metrics from real browser sessions, extending observability past the server boundary to what users actually experience. It records page performance and interaction signals — load times, web vitals, and frontend errors — and ties them back to the backend traces those interactions trigger. That front-to-back correlation is the point: a slow page can be followed straight into the service and span responsible for it.

---

## Cards in this folder

- [web-vitals.md](web-vitals.md) — the page-performance metrics that matter.
- [frontend-errors.md](frontend-errors.md) — capturing client-side failures.
- [front-to-back-correlation.md](front-to-back-correlation.md) — joining browser sessions to backend traces.

---

## References

- Official site: https://www.dash0.com
- Related: [../synthetic-monitoring/fundamentals.md](../synthetic-monitoring/fundamentals.md), [../distributed-tracing/fundamentals.md](../distributed-tracing/fundamentals.md)
