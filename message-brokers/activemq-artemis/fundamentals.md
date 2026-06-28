# ActiveMQ Artemis — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Addresses, queues, and routing](#1-addresses-queues-and-routing)
  * [2. Protocols](#2-protocols)
  * [3. Producers and consumers](#3-producers-and-consumers)
  * [4. Persistence and the journal](#4-persistence-and-the-journal)
  * [5. Clustering and high availability](#5-clustering-and-high-availability)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

Apache ActiveMQ Artemis is a high-performance, multi-protocol message broker, the next-generation successor to classic ActiveMQ. Its data model is built on addresses: producers send to an address, and a routing type decides whether the address behaves as a queue (anycast, where each message goes to one consumer) or a topic (multicast, where each message is copied to every subscriber's queue). This single model unifies point-to-point and publish-subscribe rather than treating them as separate concepts.

Artemis is notable for speaking many protocols — JMS through its core API, plus AMQP, STOMP, MQTT, and OpenWire — so clients from different ecosystems share one broker. Durability comes from a fast append-only journal, and high availability from clustering with replication. It is a strong choice when you need JMS or broad protocol support with high throughput.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Addresses, queues, and routing

The address model and anycast (queue) vs multicast (topic) routing. See [addresses-queues-and-routing.md](addresses-queues-and-routing.md).

### 2. Protocols

JMS, AMQP, STOMP, MQTT, and OpenWire over one broker. See [protocols.md](protocols.md).

### 3. Producers and consumers

Sending, acknowledgement, redelivery, priorities, and message grouping. See [producers-and-consumers.md](producers-and-consumers.md).

### 4. Persistence and the journal

The append-only journal, compaction, and paging. See [persistence-and-the-journal.md](persistence-and-the-journal.md).

### 5. Clustering and high availability

Clustering, live/backup pairing, shared-store vs replication. See [clustering-and-high-availability.md](clustering-and-high-availability.md).

### 6. Practical rule

```text
Think in addresses + routing type (anycast = queue, multicast = topic).
Use the journal for durability; pair live/backup brokers for HA.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: pick anycast vs multicast per address; use message grouping for per-key order
- TODO: acknowledge after processing; design idempotent consumers (at-least-once)

### Operations and production

- TODO: tune the journal (AIO) and paging for throughput and large backlogs
- TODO: configure live/backup HA (shared-store or replication); monitor failover

## References

- Official docs: https://activemq.apache.org/components/artemis/documentation/
- Related: [../rabbitmq/fundamentals.md](../rabbitmq/fundamentals.md)
