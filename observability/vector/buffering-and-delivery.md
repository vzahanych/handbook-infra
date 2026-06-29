# Vector — buffering and delivery

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Memory versus disk buffers](#1-memory-versus-disk-buffers)
  * [2. End-to-end acknowledgements](#2-end-to-end-acknowledgements)
  * [3. Backpressure and retries](#3-backpressure-and-retries)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Vector buffers events between components so it can batch to sinks and keep running when a destination is slow or down. Buffers can be in memory for speed or on disk for durability across restarts, configured per sink, and Vector supports end-to-end acknowledgements so an event is only considered delivered once the sink confirms it.

When a sink fails, Vector retries, and backpressure propagates upstream to avoid unbounded memory use. Configuring disk buffers and acknowledgements is how you get at-least-once reliability from the pipeline.

---

## Detailed explanation with examples

### 1. Memory versus disk buffers

- TODO: per-sink `buffer.type` memory vs disk

### 2. End-to-end acknowledgements

- TODO: `acknowledgements` so sources confirm only on sink success

### 3. Backpressure and retries

- TODO: retries; backpressure propagating upstream

### 4. Practical rule

```text
Disk buffer + acknowledgements = at-least-once across restarts.
Let backpressure flow upstream rather than buffering unbounded in memory.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: enable acknowledgements end-to-end for critical streams

### Operations and production

- TODO: size disk buffers; monitor buffer fill, retries, and dropped events

## References

- Official docs: https://vector.dev/docs/about/under-the-hood/architecture/buffering-model/
- Overview: [fundamentals.md](fundamentals.md)
