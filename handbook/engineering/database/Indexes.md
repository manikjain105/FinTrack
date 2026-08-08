---
title: Database Indexes
category: Engineering
status: Approved
version: 1.0
owner: Engineering
depends_on:
  - Database
  - Database Schema
related:
  - Migrations
  - API Design
---

# Database Indexes

> **Indexes exist to accelerate the queries users execute most frequently—not to optimize every possible query.**

---

# Purpose

This document defines the indexing strategy for FinTrack Version 1.

It specifies:

* Which indexes exist.
* Why each index exists.
* Which queries each index supports.
* When additional indexes should (or should not) be created.

Indexes are implementation details that support product performance while preserving acceptable write performance.

---

# Philosophy

Indexes improve read performance.

Indexes also increase:

* storage usage,
* insert cost,
* update cost,
* delete cost.

Every index must justify its existence.

Unused indexes should be removed.

---

# Indexing Strategy

Version 1 favors **a small number of high-value indexes**.

The expected workload is:

* frequent reads,
* moderate filtering,
* moderate sorting,
* relatively infrequent writes.

This makes selective indexing appropriate.

---

# Existing Indexes

## Transaction Date

```sql
CREATE INDEX idx_transaction_date
ON Transaction(date);
```

### Purpose

Accelerates:

* monthly views
* date filtering
* chronological sorting

---

## Transaction Category

```sql
CREATE INDEX idx_transaction_category
ON Transaction(category_id);
```

### Purpose

Optimizes:

* category reports
* dashboard summaries
* analytics
* budget calculations

---

## Transaction Type

```sql
CREATE INDEX idx_transaction_type
ON Transaction(type);
```

### Purpose

Accelerates filtering by:

* Income
* Expense

---

## Budget Month

```sql
CREATE INDEX idx_budget_month
ON Budget(month);
```

### Purpose

Optimizes retrieval of budgets for the selected month.

---

## Category Name

```sql
CREATE UNIQUE INDEX idx_category_name
ON Category(name);
```

### Purpose

Ensures fast category lookup while enforcing uniqueness.

---

# Composite Indexes

Version 1 defines one composite index.

```sql
CREATE INDEX idx_transaction_date_category
ON Transaction(date, category_id);
```

### Purpose

Supports common queries such as:

* monthly spending by category
* analytics
* dashboard summaries

---

# Query Mapping

| Query                    | Supporting Index              |
| ------------------------ | ----------------------------- |
| Transactions by Month    | idx_transaction_date          |
| Transactions by Category | idx_transaction_category      |
| Monthly Dashboard        | idx_transaction_date_category |
| Budget Lookup            | idx_budget_month              |
| Category Search          | idx_category_name             |

Every documented index should support at least one documented query.

---

# Queries That Do Not Require Indexes

Version 1 intentionally avoids indexes for:

* Notes
* Merchant
* Created At
* Updated At

Reason:

These fields are expected to have relatively low query frequency in Version 1.

Future profiling may justify additional indexes.

---

# Search Strategy

Version 1 search relies primarily on:

* indexed filters,
* in-memory filtering,
* SQLite query optimization.

Full-text search (FTS) is intentionally excluded from Version 1.

---

# Index Naming Convention

Indexes follow:

```text
idx_<table>_<column>
```

Examples:

```text
idx_transaction_date

idx_budget_month

idx_category_name
```

Composite indexes append multiple columns:

```text
idx_transaction_date_category
```

---

# Performance Considerations

Indexes should improve:

* dashboard loading,
* analytics queries,
* reports,
* transaction browsing.

Write performance remains acceptable because:

* transaction volume is moderate,
* SQLite efficiently manages small indexes.

---

# Monitoring

Before introducing a new index:

Measure:

* query execution time,
* frequency,
* table size,
* write impact.

Avoid speculative optimization.

---

# Maintenance

Whenever:

* a query changes,
* a table changes,
* a feature changes,

review the related indexes.

Unused indexes should be removed.

---

# Future Indexes

Future versions may introduce indexes for:

* Merchant
* Goals
* Attachments
* Recurring Transactions
* Investment Holdings

Only after profiling demonstrates a measurable benefit.

---

# Acceptance Criteria

The indexing strategy is complete when:

* Every index has a documented purpose.
* Every documented query is supported appropriately.
* Naming conventions are followed.
* Composite indexes are justified.
* No unnecessary indexes exist.

---

# Goal

The indexing strategy should make FinTrack feel fast without sacrificing maintainability.

Every index should exist because it solves a demonstrated performance problem—not because it seems useful.
