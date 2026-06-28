# Neo4j — Cypher basics

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Pattern matching](#1-pattern-matching)
  * [2. Filtering and writing](#2-filtering-and-writing)
  * [3. Variable-length paths](#3-variable-length-paths)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Cypher is Neo4j's declarative query language, and its defining feature is ASCII-art pattern matching: you draw the shape of the data you want with `MATCH (a)-[:REL]->(b)` and the engine finds every subgraph that fits. Around that core you use `WHERE` to filter, `RETURN` to project results, and `MERGE`, `SET`, and `DELETE` to write.

Patterns can be variable-length, so you can ask for paths of any depth between two nodes — the kind of question that is awkward in SQL. Thinking in patterns rather than joins is the mental shift Cypher requires.

---

## Detailed explanation with examples

### 1. Pattern matching

- TODO: `MATCH (a)-[:REL]->(b) RETURN ...`

### 2. Filtering and writing

- TODO: `WHERE`, `RETURN`, `MERGE`, `SET`, `DELETE`

### 3. Variable-length paths

- TODO: `[:REL*1..3]`; shortest paths

### 4. Practical rule

```text
Describe the pattern you want; let Cypher find matching subgraphs.
Anchor MATCH on an indexed property to start the traversal cheaply.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: anchor queries on indexed properties; bound variable-length paths

### Operations and production

- TODO: `PROFILE` queries; avoid unbounded `*` traversals in production

## References

- Official docs: https://neo4j.com/docs/cypher-manual/
- Overview: [fundamentals.md](fundamentals.md)
