# NATS — JetStream persistence

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Streams](#1-streams)
  * [2. Consumers](#2-consumers)
  * [3. Delivery guarantees](#3-delivery-guarantees)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

JetStream is the persistence and streaming layer of NATS, and it introduces two main objects: streams and consumers. A stream captures and stores messages published to a set of subjects, with configurable retention by age, size, or interest, so they can be replayed later.

A consumer is a view over a stream that tracks delivery and acknowledgement, available in push or pull form, giving at-least-once or effectively exactly-once delivery. This is what lets NATS act as a durable queue or event log while keeping the same subject-based addressing as core NATS.

---

## Detailed explanation with examples

### 1. Streams

- TODO: capture subjects; retention by age/size/interest

### 2. Consumers

- TODO: push vs pull; durable vs ephemeral; ack policies

### 3. Delivery guarantees

- TODO: at-least-once; dedup window for effectively-once

### 4. Practical rule

```text
Stream = stored subjects; consumer = tracked, acked view over it.
Use pull consumers + explicit acks for reliable work processing.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: pick retention policy per use; ack explicitly; design idempotent consumers

### Operations and production

- TODO: size stream storage/limits; replicate streams; monitor ack pending/redelivery

## References

- Official docs: https://docs.nats.io/nats-concepts/jetstream
- Overview: [fundamentals.md](fundamentals.md)
