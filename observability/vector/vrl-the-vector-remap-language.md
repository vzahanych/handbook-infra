# Vector — VRL, the Vector Remap Language

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The remap transform](#1-the-remap-transform)
  * [2. What VRL does](#2-what-vrl-does)
  * [3. Compiled and safe](#3-compiled-and-safe)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Instrumentation and configuration](#instrumentation-and-configuration)
  * [Operations and production](#operations-and-production)

## Core idea

VRL, the Vector Remap Language, is a small expression language built specifically for transforming observability events, and it is the heart of Vector's flexibility. In a `remap` transform you write VRL to parse fields, rename and delete keys, enrich, conditionally route, and reshape events, with the language designed to be fast and safe — it is compiled and checked rather than interpreted loosely.

It replaces the patchwork of separate parser and filter plugins other tools use with one consistent language. Learning VRL is most of learning how to do real work in Vector.

---

## Detailed explanation with examples

### 1. The remap transform

- TODO: `transforms.x.type = "remap"` with a VRL `source`

### 2. What VRL does

- TODO: parse (`parse_json`), set/delete fields, conditionals, abort/drop

### 3. Compiled and safe

- TODO: compile-time checks; fallible operations handled explicitly

### 4. Practical rule

```text
Do parsing/reshaping/routing in one VRL `remap`, not many plugins.
Handle fallible operations explicitly (VRL forces it).
```

---

## Modern best practice AI rules

### Instrumentation and configuration

- TODO: keep VRL focused and tested; handle errors rather than ignoring them

### Operations and production

- TODO: watch for VRL errors/dropped events; benchmark heavy remaps

## References

- Official docs: https://vector.dev/docs/reference/vrl/
- Overview: [fundamentals.md](fundamentals.md)
