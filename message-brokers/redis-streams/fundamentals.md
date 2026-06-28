# Redis Streams — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The stream data structure](#1-the-stream-data-structure)
  * [2. Producing and consuming entries](#2-producing-and-consuming-entries)
  * [3. Consumer groups](#3-consumer-groups)
  * [4. Trimming and retention](#4-trimming-and-retention)
  * [5. Practical rule](#5-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Redis Streams is a log data type inside Redis, giving an append-only sequence of entries that behaves like a lightweight Kafka rather than a transient pub-sub channel. Each entry has an auto-generated time-based ID, holds a set of field-value pairs, and stays in the stream until trimmed, so consumers can read history, resume from a position, and replay.

The standout feature is consumer groups, which let multiple consumers share a stream with per-consumer tracking, acknowledgement, and recovery of unprocessed entries — at-least-once delivery without a separate broker. The trade-off is that you inherit Redis's memory-first nature and single-node-per-shard model, so durability and scale depend on how Redis itself is configured.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. The stream data structure

The append-only log under one key, time-based IDs, and field-value entries. See [the-stream-data-structure.md](the-stream-data-structure.md).

### 2. Producing and consuming entries

`XADD`, `XRANGE`, and `XREAD` for appending and tailing the log. See [producing-and-consuming-entries.md](producing-and-consuming-entries.md).

### 3. Consumer groups

`XREADGROUP`, the pending list, `XACK`, and `XCLAIM` for shared at-least-once work. See [consumer-groups.md](consumer-groups.md).

### 4. Trimming and retention

`MAXLEN`/`MINID` trimming and sizing retention against memory. See [trimming-and-retention.md](trimming-and-retention.md).

### 5. Practical rule

```text
Use Streams as a lightweight log/queue inside Redis you already run.
Use consumer groups + XACK for at-least-once; trim to bound memory.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: use consumer groups for shared work; `XACK` after processing; idempotent consumers
- TODO: recover stuck work with `XAUTOCLAIM`/`XCLAIM`

### Operations and production

- TODO: trim with `MAXLEN ~`/`MINID`; size retention vs consumer lag and memory
- TODO: configure Redis persistence/replication for the durability you need

## References

- Official docs: https://redis.io/docs/data-types/streams/
- Related: [../../databases/redis/fundamentals.md](../../databases/redis/fundamentals.md)
