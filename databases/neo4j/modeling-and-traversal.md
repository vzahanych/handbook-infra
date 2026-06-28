# Neo4j — modeling and traversal

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Node, relationship, or property](#1-node-relationship-or-property)
  * [2. Avoiding super nodes](#2-avoiding-super-nodes)
  * [3. Modeling for query paths](#3-modeling-for-query-paths)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Good graph modeling comes down to deciding what is a node, what is a relationship, and what is a property, and the guiding question is how you will traverse the data. Anything you want to follow or query across should be a relationship rather than a property holding an id, since that is what unlocks index-free adjacency.

The main pitfall is the super node, a single node connected to millions of relationships, which turns every traversal through it into a bottleneck and sometimes needs to be modeled around. Because the storage is tuned for traversal, shaping the graph to match your real query paths matters more than normalization.

---

## Detailed explanation with examples

### 1. Node, relationship, or property

- TODO: follow/query across → relationship; attribute → property

### 2. Avoiding super nodes

- TODO: dense nodes as bottlenecks; modeling around them

### 3. Modeling for query paths

- TODO: shape the graph to real traversals, not normalization

### 4. Practical rule

```text
If you traverse it, make it a relationship — not a foreign-key-like property.
Watch for super nodes; model around millions of edges on one node.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: model from traversal patterns; promote queried links to relationships

### Operations and production

- TODO: detect/refactor super nodes; `PROFILE` slow traversals

## References

- Official docs: https://neo4j.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
