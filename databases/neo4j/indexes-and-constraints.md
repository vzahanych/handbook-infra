# Neo4j — indexes and constraints

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Indexes anchor traversals](#1-indexes-anchor-traversals)
  * [2. Index types](#2-index-types)
  * [3. Constraints](#3-constraints)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Indexes in Neo4j speed up the start of a traversal, because while following relationships is cheap, finding the first node by a property value still needs a lookup. You create indexes on the label-property combinations you begin queries from — range, lookup, text, point, and full-text indexes for different needs — so a `MATCH` anchored on an indexed property does not scan every node of a label.

Constraints add data integrity, with uniqueness and existence constraints ensuring, for example, that every `:User` has a unique email, and a uniqueness constraint also creates a backing index. The `PROFILE` and `EXPLAIN` keywords show whether a query uses an index or falls back to a label scan.

---

## Detailed explanation with examples

### 1. Indexes anchor traversals

- TODO: index the property you start `MATCH` on

### 2. Index types

- TODO: range, lookup, text, point, full-text

### 3. Constraints

- TODO: uniqueness (creates an index), existence, node key

### 4. Practical rule

```text
Index the properties you anchor queries on; following relationships is already fast.
Add uniqueness constraints for natural keys (they back an index).
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: create constraints/indexes before bulk import for `MERGE` performance

### Operations and production

- TODO: use `PROFILE` to confirm index usage; avoid full label scans

## References

- Official docs: https://neo4j.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
