# Dash0 synthetic monitoring — uptime and baselines

## Core idea

The stream of scheduled-check results accumulates into uptime and response-time baselines — the expected availability and latency of each monitored path. A baseline is what makes a regression detectable: a new failure or a latency creep stands out against the established normal. These baselines turn synthetic results from isolated pings into a trend that alerting and SLO reporting can act on.

---

## References

- Official site: https://www.dash0.com
- Related: [../alerting/fundamentals.md](../alerting/fundamentals.md)
