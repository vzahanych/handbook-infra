# Dash0 OpenTelemetry-native — no agent, no lock-in

## Core idea

Dash0 ships no proprietary agent, which is the mechanism behind its anti-lock-in promise. Since instrumentation is plain OpenTelemetry and the wire format is open OTLP, nothing in your code or pipeline is specific to Dash0 — you can repoint the same telemetry at a different OTLP backend without re-instrumenting a single service. This inverts the usual APM trade-off, where adopting a vendor's agent quietly couples your codebase to that vendor.

---

## References

- Official site: https://www.dash0.com
- Related: [../pricing-and-cost/fundamentals.md](../pricing-and-cost/fundamentals.md)
