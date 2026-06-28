# CockroachDB — transactions and consistency

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Serializable by default](#1-serializable-by-default)
  * [2. Distributed transactions](#2-distributed-transactions)
  * [3. Retries](#3-retries)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

CockroachDB runs transactions at serializable isolation by default, the strongest level, so concurrent transactions behave as if they ran one at a time. It achieves this across a distributed cluster, which means a transaction may touch ranges on several nodes and must coordinate them, and under contention it can be forced to retry.

Your application therefore needs a retry loop around transactions, treating retry errors as normal rather than exceptional. The payoff is correctness by default — you do not opt into strong consistency, you get it.

---

## Detailed explanation with examples

### 1. Serializable by default

- TODO: serializable isolation; what anomalies it prevents

### 2. Distributed transactions

- TODO: multi-range, multi-node coordination
- TODO: clock skew and `--max-offset`

### 3. Retries

- TODO: transaction retry errors
- TODO: client-side retry loops

### 4. Practical rule

```text
Wrap transactions in a retry loop; retryable errors are expected.
Keep transactions small to reduce contention.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: design for serializable; implement retry-on-restart logic everywhere

### Operations and production

- TODO: keep node clocks synced (NTP); monitor transaction restarts

## References

- Official docs: https://www.cockroachlabs.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
