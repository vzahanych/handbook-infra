# Redpanda — Kafka API compatibility

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The Kafka wire protocol](#1-the-kafka-wire-protocol)
  * [2. Ecosystem and tooling](#2-ecosystem-and-tooling)
  * [3. Version and feature coverage](#3-version-and-feature-coverage)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Redpanda implements the Kafka wire protocol, so producers and consumers written for Kafka connect without code changes, and tools like the console clients, Kafka Connect, and schema registries work as-is. The same topic, partition, key, offset, and consumer-group concepts apply, so the data model is identical.

Compatibility is high but tracks specific Kafka versions and a subset of APIs, so very new or peripheral Kafka features should be checked against Redpanda's support matrix. For mainstream streaming use it is a drop-in.

---

## Detailed explanation with examples

### 1. The Kafka wire protocol

- TODO: clients connect unchanged; same concepts

### 2. Ecosystem and tooling

- TODO: Kafka Connect, schema registry, console clients

### 3. Version and feature coverage

- TODO: supported API versions; checking the matrix

### 4. Practical rule

```text
Treat it as Kafka for clients and tools; verify newer/peripheral APIs.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: reuse existing Kafka client libraries and configs

### Operations and production

- TODO: validate connectors/registry compatibility before production

## References

- Official docs: https://docs.redpanda.com/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [../kafka/fundamentals.md](../kafka/fundamentals.md)
