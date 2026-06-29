# Fluent Bit — buffering and backpressure

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Memory versus filesystem buffering](#1-memory-versus-filesystem-buffering)
  * [2. Backpressure and limits](#2-backpressure-and-limits)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Because an agent must keep working when destinations slow down or fail, Fluent Bit buffers records between input and output. By default buffering is in memory, which is fast but bounded by RAM, and filesystem buffering can be enabled to persist data and survive restarts or longer outages.

When a destination cannot keep up, backpressure builds, and Fluent Bit applies limits and pause/resume so it does not exhaust memory. Configuring buffering and limits to match your reliability needs is the main operational concern.

---

## Detailed explanation with examples

### 1. Memory versus filesystem buffering

- TODO: memory (fast, volatile) vs `storage.type filesystem` (durable)

### 2. Backpressure and limits

- TODO: `Mem_Buf_Limit`, `storage.max_chunks_up`; pause/resume

### 3. Practical rule

```text
Enable filesystem buffering for durability; set memory limits to avoid OOM.
Backpressure should pause inputs, not crash the agent.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: set `Mem_Buf_Limit` per input; enable filesystem storage for critical streams

### Operations and production

- TODO: size buffer storage; alert on retries/drops and buffer saturation

## References

- Official docs: https://docs.fluentbit.io/manual/administration/buffering-and-storage
- Overview: [fundamentals.md](fundamentals.md)
