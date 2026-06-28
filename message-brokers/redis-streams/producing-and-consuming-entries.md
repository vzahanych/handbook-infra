# Redis Streams — producing and consuming entries

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Appending with XADD](#1-appending-with-xadd)
  * [2. Reading with XREAD](#2-reading-with-xread)
  * [3. Fan-out by position](#3-fan-out-by-position)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Producing to a stream is a single `XADD` that appends an entry and returns its ID, and the simplest consumption is `XREAD`, which reads entries after a given ID and can block waiting for new ones. Used this way, every consumer sees every entry and tracks its own position by remembering the last ID it processed, which is the fan-out pattern.

This is enough for broadcast-style consumption and for a single worker tailing a log. When you need several workers to divide the entries instead of all seeing them, you move to consumer groups.

---

## Detailed explanation with examples

### 1. Appending with XADD

- TODO: `XADD key * field value ...`; returns the entry ID

### 2. Reading with XREAD

- TODO: `XREAD BLOCK ... STREAMS key id`; tailing new entries

### 3. Fan-out by position

- TODO: each consumer tracks its own last-ID; everyone sees all entries

### 4. Practical rule

```text
XADD to append; XREAD (blocking) to tail.
Plain XREAD = fan-out (all see all); use groups to divide work.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: persist the last processed ID for resume; use blocking reads to avoid polling

### Operations and production

- TODO: watch for slow consumers falling behind trimming

## References

- Official docs: https://redis.io/docs/data-types/streams/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [consumer-groups.md](consumer-groups.md)
