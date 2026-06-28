# MongoDB — embedding versus referencing

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. When to embed](#1-when-to-embed)
  * [2. When to reference](#2-when-to-reference)
  * [3. Avoiding unbounded growth](#3-avoiding-unbounded-growth)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

The defining modeling decision in MongoDB is whether to embed related data inside one document or store it in a separate document and reference it by id. Embedding keeps data you read and write together in one place, so a single read returns everything and there is no join, which is ideal for one-to-few relationships and data with the same lifecycle.

Referencing suits relationships that are large, grow without bound, or are shared across many parents, since embedding them would bloat documents toward the 16 MB limit. Good schemas mix both, driven by how the application actually reads the data rather than by normalization rules.

---

## Detailed explanation with examples

### 1. When to embed

- TODO: one-to-few, read-together, same lifecycle

### 2. When to reference

- TODO: one-to-many/many-to-many, shared, large
- TODO: manual joins or `$lookup`

### 3. Avoiding unbounded growth

- TODO: never embed an ever-growing array
- TODO: the subset / outlier patterns

### 4. Practical rule

```text
Embed what you read together; reference what grows or is shared.
Never let an embedded array grow without bound.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: model from read patterns; mix embed + reference deliberately

### Operations and production

- TODO: watch for documents bloated by growing embedded arrays

## References

- Official docs: https://www.mongodb.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
