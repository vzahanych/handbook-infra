# Neo4j — fundamentals

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The property graph model](#1-the-property-graph-model)
  * [2. Nodes and relationships](#2-nodes-and-relationships)
  * [3. Cypher basics](#3-cypher-basics)
  * [4. Indexes and constraints](#4-indexes-and-constraints)
  * [5. Modeling and traversal](#5-modeling-and-traversal)
  * [6. Transactions](#6-transactions)
  * [7. Practical rule](#7-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Neo4j is a native graph database. It stores data as nodes connected by relationships, and both nodes and relationships can carry properties. Instead of joining tables, you follow relationships directly, which makes deeply connected queries fast. You query it with Cypher, a pattern-matching language.

Relationships are first-class and stored directly with the nodes they connect, so following a connection is a pointer hop rather than the lookup a relational join pays for. That advantage only holds if you model connections as relationships; burying them in properties to mimic foreign keys throws it away. The other thing to watch is the super node — a single node wired to millions of relationships turns every traversal through it into a bottleneck.

---

## Detailed explanation with examples

Each block below has a dedicated deep-dive card in this folder. This section is the map; follow the links for detail.

### 1. The property graph model

Nodes, relationships, properties, labels, and index-free adjacency. See [the-property-graph-model.md](the-property-graph-model.md).

### 2. Nodes and relationships

`CREATE`/`MERGE`, direction and type, and properties on edges. See [nodes-and-relationships.md](nodes-and-relationships.md).

### 3. Cypher basics

Pattern matching, filtering/writing, and variable-length paths. See [cypher-basics.md](cypher-basics.md).

### 4. Indexes and constraints

Indexes that anchor traversals, index types, and constraints. See [indexes-and-constraints.md](indexes-and-constraints.md).

### 5. Modeling and traversal

Node vs relationship vs property, super nodes, and modeling for query paths. See [modeling-and-traversal.md](modeling-and-traversal.md).

### 6. Transactions

ACID transactions and causal clustering. See [transactions.md](transactions.md).

### 7. Practical rule

```text
Model relationships as relationships, not foreign-key-like properties.
Index the properties you start traversals from.
Watch for super nodes; verify traversals with PROFILE.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: use relationships for connections; properties for attributes
- TODO: `MERGE` with constraints to avoid duplicate nodes
- TODO: index lookup properties; anchor `MATCH` on indexed fields

### Operations and production

- TODO: create uniqueness constraints (they back an index)
- TODO: size page cache to the graph; use causal clustering for HA
- TODO: monitor slow Cypher with `PROFILE`; watch for super nodes

## References

- Official docs: https://neo4j.com/docs/
- Related: [the-property-graph-model.md](the-property-graph-model.md)
