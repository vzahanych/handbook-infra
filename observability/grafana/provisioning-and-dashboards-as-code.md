# Grafana — provisioning and dashboards as code

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Provisioning from files](#1-provisioning-from-files)
  * [2. Dashboards as code](#2-dashboards-as-code)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Grafana can be configured entirely from files instead of clicking in the UI, which is how it stays reproducible. Provisioning loads data sources, dashboards, and alerting from YAML and JSON on startup, so an environment can be stood up identically and changes are reviewed in version control.

Dashboards exported as JSON, or generated with tools like Grafonnet and the Terraform provider, become code that lives beside the services they monitor. Adopting dashboards-as-code is what prevents drift and lost dashboards as a Grafana install grows.

---

## Detailed explanation with examples

### 1. Provisioning from files

- TODO: provisioning YAML for data sources/dashboards/alerting

### 2. Dashboards as code

- TODO: JSON in git; Grafonnet/Jsonnet; Terraform provider

### 3. Practical rule

```text
Provision data sources, dashboards, and alerts from files in version control.
Generate dashboards as code to avoid UI drift and lost work.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: keep dashboard JSON/generators in the service repo

### Operations and production

- TODO: make UI read-mostly; reconcile from provisioning; review changes in PRs

## References

- Official docs: https://grafana.com/docs/grafana/latest/administration/provisioning/
- Overview: [fundamentals.md](fundamentals.md)
