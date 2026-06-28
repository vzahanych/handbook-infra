# ActiveMQ Artemis — protocols

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The supported protocols](#1-the-supported-protocols)
  * [2. One model underneath](#2-one-model-underneath)
  * [3. Practical rule](#3-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

A defining strength of Artemis is its multi-protocol support, letting clients written for different standards connect to the same broker. It implements JMS through its core API for Java applications, AMQP for cross-language interoperability, STOMP for simple text-based clients, MQTT for IoT devices, and OpenWire for compatibility with classic ActiveMQ clients.

Because they all map onto the same address-and-queue model underneath, a message published over one protocol can be consumed over another. This makes Artemis a good integration hub when you must bridge heterogeneous systems.

---

## Detailed explanation with examples

### 1. The supported protocols

- TODO: JMS/core, AMQP, STOMP, MQTT, OpenWire

### 2. One model underneath

- TODO: all map to addresses/queues; cross-protocol consumption

### 3. Practical rule

```text
Use one Artemis broker as an integration hub across JMS/AMQP/STOMP/MQTT/OpenWire.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: pick the protocol per client ecosystem; rely on the shared address model

### Operations and production

- TODO: enable only the protocols/ports you need; secure each acceptor

## References

- Official docs: https://activemq.apache.org/components/artemis/documentation/
- Overview: [fundamentals.md](fundamentals.md)
