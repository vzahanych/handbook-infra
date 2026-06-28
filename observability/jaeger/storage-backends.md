# Jaeger — storage backends

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Production backends](#1-production-backends)
  * [2. Development backends](#2-development-backends)
  * [3. Indexing and search](#3-indexing-and-search)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Jaeger stores traces in pluggable backends, and the choice shapes its search capability and operational burden. Production deployments commonly use Cassandra or Elasticsearch/OpenSearch, which index spans so the UI can search by service, operation, tag, and duration, while in-memory and Badger backends suit development.

Because these backends index spans, Jaeger offers richer attribute search out of the box than an index-light store, at the cost of running and scaling that database. Selecting and sizing the storage backend is the central operational decision.

---

## Detailed explanation with examples

### 1. Production backends

- TODO: Cassandra, Elasticsearch/OpenSearch

### 2. Development backends

- TODO: in-memory, Badger

### 3. Indexing and search

- TODO: span indexing enables service/op/tag/duration search

### 4. Practical rule

```text
Use Cassandra or Elasticsearch in production; in-memory/Badger only for dev.
The backend defines both search power and operational cost.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: tag spans to exploit backend search

### Operations and production

- TODO: size/scale the backend to span volume; set retention; back it up

## References

- Official docs: https://www.jaegertracing.io/docs/
- Overview: [fundamentals.md](fundamentals.md)
