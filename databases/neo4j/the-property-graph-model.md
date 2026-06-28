# Neo4j — the property graph model

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Nodes, relationships, properties](#1-nodes-relationships-properties)
  * [2. Labels and relationship types](#2-labels-and-relationship-types)
  * [3. Index-free adjacency](#3-index-free-adjacency)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Neo4j stores data as a property graph, made of nodes that represent entities and relationships that represent the typed, directed connections between them, with both able to hold properties as key-value pairs. Nodes are grouped by labels, like `:Person` or `:Order`, which act as the categories you query against, and every relationship has a type and a direction.

Unlike a relational database where connections are inferred at query time by matching foreign keys, Neo4j stores each relationship as a direct pointer between its nodes. This is called index-free adjacency, and it is why walking a chain of connections stays fast no matter how large the graph grows.

---

## Detailed explanation with examples

### 1. Nodes, relationships, properties

- TODO: nodes = entities; relationships = typed directed edges; properties on both

### 2. Labels and relationship types

- TODO: labels group nodes; relationship types name edges

### 3. Index-free adjacency

- TODO: stored pointers vs join-time matching; why traversal is fast

### 4. Practical rule

```text
Model entities as nodes, connections as typed relationships, attributes as properties.
Lean on index-free adjacency: traversal is cheap, joins are not needed.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: use labels as query categories; give relationships clear types/directions

### Operations and production

- TODO: size page cache to hold the graph for fast traversal

## References

- Official docs: https://neo4j.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
