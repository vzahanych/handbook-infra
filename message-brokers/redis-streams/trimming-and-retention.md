# Redis Streams — trimming and retention

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. MAXLEN and MINID](#1-maxlen-and-minid)
  * [2. Trimming is independent of acks](#2-trimming-is-independent-of-acks)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Because stream entries persist in memory until removed, you must trim the stream or it grows without bound. `XADD` can trim as it writes using `MAXLEN` to cap the number of entries or `MINID` to drop entries older than an ID, and the approximate (`~`) form trims efficiently in whole nodes.

Trimming is independent of consumption: entries are removed by these policies, not when acknowledged, so a slow or absent consumer can still lose history if trimming outpaces it. Sizing retention against consumer speed and available memory is the key operational concern.

---

## Detailed explanation with examples

### 1. MAXLEN and MINID

- TODO: `XADD ... MAXLEN ~ N`; `XTRIM`; `MINID`

### 2. Trimming is independent of acks

- TODO: entries dropped by policy, not on `XACK`; slow consumers can lose data

### 3. Practical rule

```text
Always trim (MAXLEN ~ / MINID) to bound memory.
Size retention above your slowest consumer's lag.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: don't assume entries persist until acked — they don't

### Operations and production

- TODO: set trimming policy; monitor consumer lag vs trim point and memory

## References

- Official docs: https://redis.io/docs/data-types/streams/
- Overview: [fundamentals.md](fundamentals.md)
