# Prometheus — the pull model and scraping

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Scraping /metrics](#1-scraping-metrics)
  * [2. Service discovery](#2-service-discovery)
  * [3. The Pushgateway exception](#3-the-pushgateway-exception)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Prometheus collects metrics by pulling rather than receiving pushes: it is configured with a set of targets, and on a fixed interval it makes an HTTP request to each target's `/metrics` endpoint and parses the numbers it finds there. Targets are discovered statically or through service discovery integrations with Kubernetes, cloud APIs, and others, so the target list tracks changing infrastructure automatically.

Because Prometheus initiates the scrape, it always knows whether a target is up, and the `up` metric reflects scrape success. Short-lived jobs that cannot be scraped push to a Pushgateway instead, which is the documented exception to the pull model.

---

## Detailed explanation with examples

### 1. Scraping /metrics

- TODO: scrape interval; exposition format; `up` metric

### 2. Service discovery

- TODO: static configs vs SD (Kubernetes, cloud); relabeling

### 3. The Pushgateway exception

- TODO: short-lived/batch jobs push; caveats

### 4. Practical rule

```text
Expose /metrics and let Prometheus scrape; use SD for dynamic targets.
Use Pushgateway only for short-lived batch jobs.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: prefer pull + SD; use relabeling to shape targets/labels

### Operations and production

- TODO: alert on scrape failures (`up == 0`); avoid Pushgateway for long-lived services

## References

- Official docs: https://prometheus.io/docs/
- Overview: [fundamentals.md](fundamentals.md)
