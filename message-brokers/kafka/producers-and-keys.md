# Kafka — producers and keys

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Appending records](#1-appending-records)
  * [2. Keys and partitioning](#2-keys-and-partitioning)
  * [3. Acks and idempotence](#3-acks-and-idempotence)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

A producer appends records to a topic, and each record may carry a key. The key matters because Kafka hashes it to choose a partition, so all records with the same key land on the same partition and therefore stay in order relative to one another. A record with no key is spread across partitions for balance, giving up per-key ordering.

How safely a record is written is controlled by the producer's acknowledgement setting and idempotence: `acks=all` waits for the in-sync replicas, and idempotent producers avoid duplicate records on retry. Choosing the key and the acks together is how you trade ordering, balance, and durability.

---

## Detailed explanation with examples

### 1. Appending records

- TODO: batching, compression, throughput
- TODO: record structure (key, value, headers, timestamp)

### 2. Keys and partitioning

- TODO: key hashing → partition; same key → same partition → ordering
- TODO: null key → round-robin/sticky balancing

### 3. Acks and idempotence

- TODO: `acks=0/1/all`; `min.insync.replicas`
- TODO: idempotent producer; transactions for exactly-once

### 4. Practical rule

```text
Key by the entity you need ordered together.
Use acks=all + idempotence for durable, duplicate-free writes.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: choose keys for ordering + even distribution; avoid hot keys
- TODO: enable idempotence; use transactions only when you need atomic writes

### Operations and production

- TODO: tune batch size/linger for throughput; monitor producer error/retry rates

## References

- Official docs: https://kafka.apache.org/documentation/
- Overview: [fundamentals.md](fundamentals.md)
