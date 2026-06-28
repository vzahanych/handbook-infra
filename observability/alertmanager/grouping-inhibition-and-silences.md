# Alertmanager — grouping, inhibition, and silences

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Grouping](#1-grouping)
  * [2. Inhibition](#2-inhibition)
  * [3. Silences](#3-silences)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Three features keep alert noise under control. Grouping collects alerts that share chosen labels into a single notification, so one notification covers a whole class of failures instead of hundreds of separate pages. Inhibition suppresses lower-priority alerts when a related higher-priority one is firing — if a whole cluster is down, you do not also want every per-node alert.

Silences are temporary, manually-created mutes that match alerts by label, used during maintenance or known incidents. Used together, these turn a flood of raw alerts into a manageable signal.

---

## Detailed explanation with examples

### 1. Grouping

- TODO: `group_by`; one notification per group

### 2. Inhibition

- TODO: inhibit_rules; suppress low-sev when high-sev fires

### 3. Silences

- TODO: matcher-based, time-bounded mutes (maintenance)

### 4. Practical rule

```text
Group related alerts; inhibit cascades; silence during maintenance.
Make noise the exception, not the norm.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: group by service/cluster; define inhibition for known cascades

### Operations and production

- TODO: use scheduled silences for maintenance; audit long-lived silences

## References

- Official docs: https://prometheus.io/docs/alerting/latest/configuration/
- Overview: [fundamentals.md](fundamentals.md)
