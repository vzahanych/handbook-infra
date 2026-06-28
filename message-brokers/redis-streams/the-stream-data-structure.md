# Redis Streams — the stream data structure

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Append-only log under one key](#1-append-only-log-under-one-key)
  * [2. Entry IDs](#2-entry-ids)
  * [3. Field-value entries](#3-field-value-entries)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

A Redis stream is an append-only log stored under a single key, where each entry gets a monotonically increasing ID of the form milliseconds-sequence, such as `1680000000000-0`. An entry is not a single value but a set of field-value pairs, like a small record, which makes streams a natural fit for events with structured payloads.

You append with `XADD`, read ranges with `XRANGE`, and read new entries with `XREAD`, treating the ID as your cursor. Because entries persist until explicitly trimmed, the stream is a replayable history rather than a fire-and-forget channel.

---

## Detailed explanation with examples

### 1. Append-only log under one key

- TODO: one Redis key = one stream; ordered entries

### 2. Entry IDs

- TODO: `ms-seq` IDs; auto vs explicit; cursor semantics

### 3. Field-value entries

- TODO: each entry is a small record of field-value pairs

### 4. Practical rule

```text
Treat the stream as a replayable log keyed by entry ID.
Model each entry as a structured record (field-value pairs).
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: use the entry ID as the resume cursor; design clear field schemas

### Operations and production

- TODO: remember a stream lives in one shard's memory

## References

- Official docs: https://redis.io/docs/data-types/streams/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [producing-and-consuming-entries.md](producing-and-consuming-entries.md)
