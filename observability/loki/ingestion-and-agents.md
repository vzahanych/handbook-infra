# Loki — ingestion and agents

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Agents](#1-agents)
  * [2. Labelling at ingestion](#2-labelling-at-ingestion)
  * [3. Pipelines](#3-pipelines)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Logs reach Loki through agents that collect, label, and ship them, with Promtail and the Grafana Agent (now Alloy) being the common choices, and OpenTelemetry also supported. The agent's job is to discover log sources, attach the right labels — often from Kubernetes metadata — and push lines to Loki, optionally pre-processing them in a pipeline.

Because labels are assigned at ingestion, the agent configuration is where much of your label discipline lives. Getting collection and labelling right at this stage is what makes the data usable later.

---

## Detailed explanation with examples

### 1. Agents

- TODO: Promtail, Grafana Alloy, OpenTelemetry Collector

### 2. Labelling at ingestion

- TODO: service discovery; Kubernetes metadata → labels

### 3. Pipelines

- TODO: parsing/relabeling stages before push

### 4. Practical rule

```text
Assign a small, bounded label set at the agent; drop noisy labels there.
Pre-parse only what you must; leave high-variety data in the line.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: enforce the label scheme in agent config; avoid per-pod dynamic labels

### Operations and production

- TODO: monitor agent push errors and backpressure; size batch/timeout

## References

- Official docs: https://grafana.com/docs/loki/latest/send-data/
- Overview: [fundamentals.md](fundamentals.md)
