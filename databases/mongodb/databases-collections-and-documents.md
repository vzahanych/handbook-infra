# MongoDB — databases, collections, and documents

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. The three levels](#1-the-three-levels)
  * [2. The _id field](#2-the-_id-field)
  * [3. Schema flexibility and validation](#3-schema-flexibility-and-validation)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

MongoDB organizes data in three levels that loosely mirror the relational world: a database holds collections, and a collection holds documents, where a document is the record you actually read and write. The mapping is collection-to-table and document-to-row, but the comparison stops at the schema, because documents in one collection need not share the same fields.

Every document carries a unique `_id`, generated as an `ObjectId` if you do not supply one, which serves as its primary key and is always indexed. You can layer optional schema validation onto a collection when you want to constrain that flexibility.

---

## Detailed explanation with examples

### 1. The three levels

- TODO: database → collection → document
- TODO: collection ≈ table, document ≈ row (with flexible fields)

### 2. The _id field

- TODO: `ObjectId` generation; supplying your own `_id`
- TODO: `_id` is always indexed and unique

### 3. Schema flexibility and validation

- TODO: documents need not share fields
- TODO: JSON Schema validation rules on a collection

### 4. Practical rule

```text
Collections are flexible, not schemaless by accident — add validation when fields matter.
Let MongoDB generate _id unless you have a meaningful natural key.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: add schema validation for important collections
- TODO: design collections around access patterns, not entities

### Operations and production

- TODO: keep `_id` monotonic-ish (ObjectId) for insert locality

## References

- Official docs: https://www.mongodb.com/docs/
- Overview: [fundamentals.md](fundamentals.md)
