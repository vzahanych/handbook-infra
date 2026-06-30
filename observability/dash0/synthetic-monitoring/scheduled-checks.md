# Dash0 synthetic monitoring — scheduled checks

## Core idea

Scheduled checks are scripted probes that run on a fixed interval against an endpoint or user journey, exercising the path the way a client would. Running continuously and from outside, they detect failures during quiet periods when no real traffic would reveal them. Each run produces a pass/fail and a timing, which feeds both alerting and the availability baseline.

---

## References

- Official site: https://www.dash0.com
- Related: [uptime-and-baselines.md](uptime-and-baselines.md)
