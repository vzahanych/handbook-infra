# Redis Streams — consumer groups

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Group cursor and XREADGROUP](#1-group-cursor-and-xreadgroup)
  * [2. Pending entries and XACK](#2-pending-entries-and-xack)
  * [3. Claiming stale work](#3-claiming-stale-work)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Consumer groups turn a Redis stream into a shared work queue with reliability. A group has its own cursor into the stream, and `XREADGROUP` hands each new entry to exactly one consumer in the group, so work is distributed rather than duplicated.

Delivered-but-unacknowledged entries are tracked in a pending entries list, and a consumer confirms completion with `XACK`; if a consumer dies, another can claim its stale pending entries with `XCLAIM` (or `XAUTOCLAIM`), giving at-least-once delivery and recovery. This is the feature that makes Streams a real alternative to a dedicated broker for many workloads.

---

## Detailed explanation with examples

### 1. Group cursor and XREADGROUP

- TODO: `XGROUP CREATE`; `XREADGROUP`; one entry → one consumer

### 2. Pending entries and XACK

- TODO: pending entries list (PEL); `XACK` after processing

### 3. Claiming stale work

- TODO: `XCLAIM`/`XAUTOCLAIM` to recover dead consumers' entries

### 4. Practical rule

```text
Use a group for shared work; XACK only after success; recover with XAUTOCLAIM.
Design consumers to be idempotent (at-least-once).
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: idempotent handlers; `XACK` post-success; periodic `XAUTOCLAIM`

### Operations and production

- TODO: monitor PEL size and idle pending entries; alert on growth

## References

- Official docs: https://redis.io/docs/data-types/streams/
- Overview: [fundamentals.md](fundamentals.md)
