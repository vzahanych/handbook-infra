# Elasticsearch — the inverted index

## Contents

* [Core idea](#core-idea)
* [Detailed explanation with examples](#detailed-explanation-with-examples)

  * [1. Terms to documents](#1-terms-to-documents)
  * [2. Analysis and analyzers](#2-analysis-and-analyzers)
  * [3. Doc values for sort and aggregations](#3-doc-values-for-sort-and-aggregations)
  * [4. Practical rule](#4-practical-rule)
* [Modern best practice AI rules](#modern-best-practice-ai-rules)

  * [Data modeling and access](#data-modeling-and-access)
  * [Operations and production](#operations-and-production)

## Core idea

Full-text search is fast in Elasticsearch because of the inverted index, a structure that maps each term to the list of documents containing it, so finding every document with a word is a direct lookup rather than a scan. Building it requires analysis: text fields are run through an analyzer that lowercases, tokenizes, and otherwise normalizes the text into the terms that get indexed, which is why the same analyzer must apply at query time for matches to work.

Sorting and aggregations use a complementary column-oriented structure called doc values rather than the inverted index. Understanding that analysis happens on the way in is what explains why `text` and `keyword` behave so differently.

---

## Detailed explanation with examples

### 1. Terms to documents

- TODO: term → posting list; direct lookups

### 2. Analysis and analyzers

- TODO: tokenization, lowercasing, stemming
- TODO: same analyzer at index and query time

### 3. Doc values for sort and aggregations

- TODO: columnar doc values; why `keyword` aggregates and `text` doesn't

### 4. Practical rule

```text
Analysis happens at index time — choose analyzers deliberately.
Use keyword/doc_values for sort and aggregations, text for relevance search.
```

---

## Modern best practice AI rules

### Data modeling and access

- TODO: pick analyzers per field; keep index- and query-time analysis consistent

### Operations and production

- TODO: disable doc values on fields never sorted/aggregated to save space

## References

- Official docs: https://www.elastic.co/guide/
- Overview: [fundamentals.md](fundamentals.md)
