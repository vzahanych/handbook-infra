# Grafana — alerting

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Alert rules](#1-alert-rules)
  * [2. Notification policies and contact points](#2-notification-policies-and-contact-points)
  * [3. Grafana versus Prometheus alerting](#3-grafana-versus-prometheus-alerting)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Grafana's unified alerting lets you define alert rules directly on data-source queries and route the resulting notifications, all within Grafana rather than per-backend. An alert rule periodically evaluates a query condition and, when it is breached for a set duration, fires, after which notification policies decide where it goes and contact points deliver it.

This sits alongside Prometheus's own alerting rather than replacing it, and which to use depends on whether you want alerts defined in Grafana or in Prometheus. Designing clear conditions and routing is the same discipline as with Alertmanager.

---

## Detailed explanation with examples

### 1. Alert rules

- TODO: query condition + `for` duration; multi-source rules

### 2. Notification policies and contact points

- TODO: routing tree; contact points (email, Slack, PagerDuty)

### 3. Grafana versus Prometheus alerting

- TODO: where to define alerts; trade-offs

### 4. Practical rule

```text
Define alerts where they belong (Grafana vs Prometheus), not in both.
Use a `for` duration and clear routing to the right contact points.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: meaningful conditions/labels; avoid duplicate alerts across Grafana and Prometheus

### Operations and production

- TODO: provision alert rules/policies as code; test contact points

## References

- Official docs: https://grafana.com/docs/grafana/latest/alerting/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [../alertmanager/fundamentals.md](../alertmanager/fundamentals.md)
