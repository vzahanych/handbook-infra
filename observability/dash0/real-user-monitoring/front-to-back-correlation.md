# Dash0 website monitoring — front-to-back correlation

## Core idea

The defining capability is correlating a browser session with the backend traces its interactions trigger, so the frontend and server views are one continuous picture. Propagating trace context from the page into the requests it makes lets a slow or failing interaction be followed straight into the responsible service and span. This is what closes the usual blind spot between "the page is slow for users" and "this backend call is why."

---

## References

- Official site: https://www.dash0.com
- Related: [../distributed-tracing/spans-and-context.md](../distributed-tracing/spans-and-context.md)
