# NATS — subjects and pub-sub

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The subject namespace](#1-the-subject-namespace)
  * [2. Wildcards](#2-wildcards)
  * [3. Ephemeral delivery](#3-ephemeral-delivery)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Subjects are the addressing scheme of NATS: every message is published to a subject, a dot-separated string like `sensors.room1.temp`, and subscribers express interest in subjects, optionally using the `*` wildcard for a single token or `>` for the rest. There is no need to pre-create subjects; they exist implicitly when used, which makes the namespace cheap and dynamic.

In core NATS this is pure publish-subscribe with no storage: a message goes only to subscribers connected at that moment. Designing a clear subject hierarchy is the main modeling task, because routing and security are built on it.

---

## Detailed explanation with examples

### 1. The subject namespace

- TODO: dot-delimited subjects; implicit creation

### 2. Wildcards

- TODO: `*` (one token), `>` (rest)

### 3. Ephemeral delivery

- TODO: no storage in core NATS; only current subscribers receive

### 4. Practical rule

```text
Design hierarchical subjects (domain.entity.event); use wildcards to subscribe broadly.
Core NATS delivers only to currently-connected subscribers.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: plan a consistent subject taxonomy; scope wildcards carefully

### Operations and production

- TODO: use subject-based authorization to scope access

## References

- Official docs: https://docs.nats.io/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [messaging-patterns.md](messaging-patterns.md)
