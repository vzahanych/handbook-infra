# NATS — messaging patterns

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Publish-subscribe](#1-publish-subscribe)
  * [2. Request-reply](#2-request-reply)
  * [3. Queue groups](#3-queue-groups)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

On top of subjects, core NATS supports a few fundamental patterns. Plain publish-subscribe broadcasts a message to every interested subscriber. Request-reply lets a client publish a request and receive a direct response using a temporary reply subject, which makes NATS usable as a fast RPC layer. Queue groups let multiple subscribers share a subject so that each message goes to only one member of the group, providing load-balanced work distribution.

These patterns are all ephemeral and in-memory, so they trade durability for speed.

---

## Detailed explanation with examples

### 1. Publish-subscribe

- TODO: broadcast to all subscribers

### 2. Request-reply

- TODO: reply subject; NATS as fast RPC

### 3. Queue groups

- TODO: one message → one group member; load balancing

### 4. Practical rule

```text
pub-sub = broadcast, request-reply = RPC, queue group = load-balanced work.
All ephemeral — use JetStream if you need durability.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: use queue groups for scalable workers; set request timeouts

### Operations and production

- TODO: watch for slow consumers dropping messages

## References

- Official docs: https://docs.nats.io/
- Overview: [fundamentals.md](fundamentals.md)
