# InfluxDB — tags and fields

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Tags are indexed metadata](#1-tags-are-indexed-metadata)
  * [2. Fields hold the values](#2-fields-hold-the-values)
  * [3. Timestamps and precision](#3-timestamps-and-precision)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Every point in InfluxDB carries tags and fields, and the distinction between them is the most important modeling decision. Tags are indexed metadata, always strings, used to filter and group — things like host, region, or sensor id. Fields hold the actual measured values, can be numbers or booleans or strings, and are not indexed, so you can store them freely but cannot filter on them efficiently.

Getting this split right means putting the dimensions you query by into tags and the quantities you aggregate into fields.

---

## Detailed explanation with examples

### 1. Tags are indexed metadata

- TODO: string-only; used in `WHERE`/`GROUP BY`
- TODO: each tag-set defines a series

### 2. Fields hold the values

- TODO: numeric/bool/string values; not indexed

### 3. Timestamps and precision

- TODO: precision choice (ns/us/ms/s) and storage impact

### 4. Practical rule

```text
Tags = what you filter/group by. Fields = what you measure.
Never put unbounded values in tags.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: decide tag vs field deliberately; keep tags low-cardinality

### Operations and production

- TODO: use the coarsest acceptable timestamp precision

## References

- Official docs: https://docs.influxdata.com/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [series-and-cardinality.md](series-and-cardinality.md)
