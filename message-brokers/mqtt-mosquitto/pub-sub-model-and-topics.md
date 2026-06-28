# MQTT / Mosquitto — pub-sub model and topics

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Broker-mediated pub-sub](#1-broker-mediated-pub-sub)
  * [2. Topic hierarchy](#2-topic-hierarchy)
  * [3. Wildcards](#3-wildcards)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

MQTT messaging is purely publish-subscribe through a broker, with topics as the addressing scheme. A topic is a hierarchical, slash-separated string such as `home/livingroom/temperature`, created implicitly on use, and subscribers match against topic filters using `+` for a single level and `#` for all remaining levels.

Publishers send to a specific topic and subscribers express interest in filters, so the broker decouples the two completely. A well-designed topic hierarchy is the foundation, because it determines routing, wildcard subscriptions, and access control.

---

## Detailed explanation with examples

### 1. Broker-mediated pub-sub

- TODO: clients never talk directly; broker routes by topic

### 2. Topic hierarchy

- TODO: slash-separated levels; implicit creation

### 3. Wildcards

- TODO: `+` (single level), `#` (multi level, trailing)

### 4. Practical rule

```text
Design a consistent topic hierarchy (site/device/metric).
Subscribe with `+`/`#`; scope them and ACLs carefully.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: plan topic taxonomy; avoid overly broad `#` subscriptions

### Operations and production

- TODO: align ACLs to the topic hierarchy

## References

- Official docs: https://mosquitto.org/documentation/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [quality-of-service-levels.md](quality-of-service-levels.md)
