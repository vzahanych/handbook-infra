# Fluentd — buffering and reliability

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Memory versus file buffers](#1-memory-versus-file-buffers)
  * [2. Chunks and flushing](#2-chunks-and-flushing)
  * [3. Retries and dead-letter](#3-retries-and-dead-letter)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

Fluentd buffers events before sending them so it can batch efficiently and retry on failure, which is the basis of its reliable delivery. Buffers can be held in memory for speed or on the filesystem for durability across restarts and outages, and they are organized into chunks that are flushed to the output.

When an output fails, Fluentd retries with backoff and can route persistently-failing events to a secondary or dead-letter destination. Tuning buffer type, chunk and flush settings, and retry behavior is how you trade throughput against durability.

---

## Detailed explanation with examples

### 1. Memory versus file buffers

- TODO: `<buffer>` memory (fast) vs file (durable)

### 2. Chunks and flushing

- TODO: chunk limits; flush interval/threads

### 3. Retries and dead-letter

- TODO: retry backoff; `<secondary>` for failed chunks

### 4. Practical rule

```text
Use file buffers for durability; tune chunk/flush for throughput.
Send permanently-failing chunks to a secondary, don't drop silently.
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: size chunk limits and flush threads to output capacity

### Operations and production

- TODO: monitor buffer queue length and retry counts; alert on growth

## References

- Official docs: https://docs.fluentd.org/configuration/buffer-section
- Overview: [fundamentals.md](fundamentals.md)
