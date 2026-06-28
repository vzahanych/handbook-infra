# Neo4j — nodes and relationships

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. CREATE and MERGE](#1-create-and-merge)
  * [2. Direction and type](#2-direction-and-type)
  * [3. Properties on edges](#3-properties-on-edges)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

You build a graph by creating nodes and the relationships that join them, using `CREATE` to add new data and `MERGE` to create something only if it does not already exist, which avoids duplicates. A relationship always has a type and a direction written in the pattern, such as `(a)-[:FOLLOWS]->(b)`, though you can traverse it in either direction at query time.

Both nodes and relationships carry properties, so an edge can store its own data — a `:RATED` relationship might hold a score and a timestamp. Modeling facts as relationships rather than as foreign-key-like properties is what lets the graph do its job.

---

## Detailed explanation with examples

### 1. CREATE and MERGE

- TODO: `CREATE` vs `MERGE` (get-or-create) to avoid duplicates

### 2. Direction and type

- TODO: directed, typed edges; traversing either way

### 3. Properties on edges

- TODO: storing data on relationships (e.g. weight, timestamp)

### 4. Practical rule

```text
Use MERGE (with constraints) to avoid duplicate nodes.
Store connection data on the relationship, not duplicated on nodes.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: `MERGE` on a constrained key; model facts as relationships

### Operations and production

- TODO: batch large imports; avoid one transaction per tiny write

## References

- Official docs: https://neo4j.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
- Related: [cypher-basics.md](cypher-basics.md)
