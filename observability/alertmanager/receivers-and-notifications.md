# Alertmanager — receivers and notifications

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Receivers](#1-receivers)
  * [2. Notification templates](#2-notification-templates)
  * [3. Timing](#3-timing)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

A receiver is a named notification target, and it defines how a routed alert is actually delivered. Alertmanager ships integrations for email, Slack, PagerDuty, Opsgenie, webhooks, and more, and a single receiver can fan out to several of these.

Notification content is shaped with templates, so messages carry the alert's labels and annotations in a readable form. Timing settings on the route — group wait, group interval, and repeat interval — control when and how often a receiver is notified, which is how you balance promptness against spam.

---

## Detailed explanation with examples

### 1. Receivers

- TODO: email, Slack, PagerDuty, Opsgenie, webhook; fan-out

### 2. Notification templates

- TODO: templating labels/annotations into messages

### 3. Timing

- TODO: group_wait/group_interval/repeat_interval effects

### 4. Practical rule

```text
Route to receivers per team/severity; template messages for readability.
Tune repeat_interval so pages are prompt but not spammy.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: keep secrets out of config; template clear, actionable messages

### Operations and production

- TODO: test each receiver; monitor notification failures

## References

- Official docs: https://prometheus.io/docs/alerting/latest/configuration/
- Overview: [fundamentals.md](fundamentals.md)
