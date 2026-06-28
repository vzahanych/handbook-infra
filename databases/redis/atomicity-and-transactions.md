# Redis — atomicity and transactions

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Single commands are atomic](#1-single-commands-are-atomic)
  * [2. MULTI, EXEC, and WATCH](#2-multi-exec-and-watch)
  * [3. Lua scripting](#3-lua-scripting)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Every individual Redis command is atomic because the server processes commands one at a time on a single thread, so a single `INCR` or `LPUSH` never interleaves with another client's command. When you need several commands to run together, `MULTI`/`EXEC` queues them and runs them as one unit, and `WATCH` adds optimistic locking so the transaction aborts if a watched key changed underneath it.

For genuinely complex atomic logic, a Lua script runs server-side as a single atomic operation, which is the idiomatic way to avoid read-modify-write races. Reaching for atomic commands or scripts instead of client-side coordination is how you keep concurrent access correct.

---

## Detailed explanation with examples

### 1. Single commands are atomic

- TODO: single-threaded command execution

### 2. MULTI, EXEC, and WATCH

- TODO: queued transactions; optimistic locking with `WATCH`
- TODO: no rollback semantics like SQL

### 3. Lua scripting

- TODO: `EVAL`; atomic server-side compound logic

### 4. Practical rule

```text
Prefer a single atomic command or a Lua script over client-side read-modify-write.
Use WATCH/MULTI/EXEC for optimistic multi-key updates.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: model counters/locks with atomic commands; avoid races by design

### Operations and production

- TODO: keep Lua scripts short (they block the single thread)

## References

- Official docs: https://redis.io/docs/interact/transactions/
- Overview: [fundamentals.md](fundamentals.md)
