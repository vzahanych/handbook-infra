# MQTT / Mosquitto — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Pub-sub model and topics](#1-pub-sub-model-and-topics)
  * [2. Quality of service levels](#2-quality-of-service-levels)
  * [3. Retained messages and last will](#3-retained-messages-and-last-will)
  * [4. Sessions and clients](#4-sessions-and-clients)
  * [5. Mosquitto broker operations](#5-mosquitto-broker-operations)
  * [6. Practical rule](#6-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Messaging and client design](#messaging-and-client-design)
  * [Operations and production](#operations-and-production)

## Core idea

MQTT is a lightweight publish-subscribe protocol designed for unreliable, low-bandwidth networks, which is why it dominates IoT and device messaging. Clients connect to a broker — Mosquitto is the common open-source one — and publish messages to hierarchical topics like `home/livingroom/temperature`, while other clients subscribe to topic filters with wildcards. The broker is the only intermediary; publishers and subscribers never talk directly.

What makes MQTT suited to flaky devices is a small set of reliability features built into the protocol: three quality-of-service levels for delivery guarantees, retained messages so a new subscriber immediately gets the last known value, last-will messages that announce unexpected disconnects, and sessions that survive brief drops. Understanding these four features is most of understanding MQTT.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. Pub-sub model and topics

Broker-mediated pub-sub and the hierarchical topic/wildcard scheme. See [pub-sub-model-and-topics.md](pub-sub-model-and-topics.md).

### 2. Quality of service levels

QoS 0/1/2 and the delivery-certainty versus overhead trade-off. See [quality-of-service-levels.md](quality-of-service-levels.md).

### 3. Retained messages and last will

Last-known-value retention and dead-client announcement. See [retained-messages-and-last-will.md](retained-messages-and-last-will.md).

### 4. Sessions and clients

Client IDs, clean vs persistent sessions, and reconnect recovery. See [sessions-and-clients.md](sessions-and-clients.md).

### 5. Mosquitto broker operations

Configuring listeners, TLS, auth, and ACLs in Mosquitto. See [mosquitto-broker-operations.md](mosquitto-broker-operations.md).

### 6. Practical rule

```text
Design a clean topic hierarchy; pick the lowest QoS that meets the need.
Use retained + last-will for state/presence; secure the broker with TLS + ACLs.
```

---

## Modern best practice AI rules

### Messaging and client design

- TODO: hierarchical topics; minimal QoS per message; retained for state, LWT for presence
- TODO: stable client IDs; persistent sessions for devices that reconnect

### Operations and production

- TODO: require TLS and real credentials; enforce per-topic ACLs
- TODO: monitor connected clients, in-flight QoS messages, and broker load

## References

- Official docs: https://mosquitto.org/documentation/
- Related: [../nats/fundamentals.md](../nats/fundamentals.md)
