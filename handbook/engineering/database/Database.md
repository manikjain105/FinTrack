---
title: Database
category: Engineering
status: Approved
version: 1.0
owner: Engineering
depends_on:
  - Architecture
  - Technology Stack
  - Engineering Principles
related:
  - Schema
  - Migrations
  - Indexes
---

# Database

> **The database is the single source of truth for all persistent financial data in FinTrack.**

---

# Purpose

This document defines the database architecture, storage philosophy, and operational principles for FinTrack.

It explains:

* Why SQLite was selected.
* How data is stored.
* How transactions are managed.
* Backup philosophy.
* Migration strategy.
* Performance expectations.

The actual table definitions are documented in **Schema.md**.

---

# Database Philosophy

FinTrack follows a **local-first** architecture.

All financial data is stored on the user's device.

Version 1 intentionally avoids:

* Cloud databases
* Remote synchronization
* Multi-user storage

The database should remain simple, reliable, and transparent.

---

# Database Engine

Version 1 uses:

| Property      | Value         |
| ------------- | ------------- |
| Engine        | SQLite        |
| Version       | SQLite 3.x    |
| ORM           | SQLAlchemy    |
| Driver        | sqlite3       |
| Database File | `fintrack.db` |

SQLite is selected because it requires no server, is highly reliable, and is well suited to a single-user desktop application.

---

# Responsibilities

The database is responsible for:

* Persisting application data.
* Preserving data integrity.
* Enforcing constraints.
* Supporting efficient queries.
* Providing transactional guarantees.

Business rules belong in the Service Layer, not in the database.

---

# Stored Data

Version 1 persists:

* Transactions
* Budgets
* Categories
* User Preferences

Future versions may include:

* Goals
* Recurring Transactions
* Attachments
* Sync Metadata

---

# Data Ownership

Users own all financial data stored by FinTrack.

The application should never modify user data without an explicit user action.

All destructive operations should require confirmation at the application level.

---

# Database Location

The application stores a single SQLite database file.

```text
database/
└── fintrack.db
```

The location should be configurable for development environments while remaining predictable for production installations.

---

# Transaction Management

All write operations should execute within a database transaction.

Typical lifecycle:

```text
Begin Transaction
        │
        ▼
Validate Input
        │
        ▼
Write Changes
        │
        ▼
Commit
```

If any step fails:

```text
Rollback
```

Partial writes must never occur.

---

# Atomic Operations

The following operations must be atomic:

* Create Transaction
* Update Transaction
* Delete Transaction
* Import Transactions
* Create Budget
* Update Budget

Either the entire operation succeeds or none of it is persisted.

---

# Integrity

The database should enforce:

* Primary keys
* Foreign keys
* Required fields
* Unique constraints where appropriate

Application logic should not rely solely on client-side validation.

---

# Identifier Strategy

Every persistent record should have a stable unique identifier.

Requirements:

* Globally unique
* Immutable
* Never reused

The exact identifier format is defined in **Schema.md**.

---

# Time Handling

All timestamps should:

* Use UTC internally.
* Be stored consistently.
* Be converted to the user's local timezone only for display.

Every persisted entity should include:

* `created_at`
* `updated_at`

where applicable.

---

# Concurrency

Version 1 assumes a single-user application.

Concurrent writes are expected to be rare.

SQLite's built-in transaction model is sufficient for the current scope.

---

# Backup Philosophy

The database should be easy to back up.

Recommended backup methods:

* Export data (CSV/PDF where appropriate).
* Copy the SQLite database file while the application is closed.

Future versions may introduce automated backup functionality.

---

# Migration Strategy

Schema changes must be managed through versioned migrations.

Migrations should:

* Be repeatable.
* Be reversible where practical.
* Never modify production data unexpectedly.

Migration implementation is documented in **Migrations.md**.

---

# Performance Strategy

The database should support:

* Fast transaction lookup.
* Efficient filtering.
* Responsive reporting.
* Smooth analytics queries.

Performance improvements should prioritize indexing and query optimization before introducing architectural complexity.

---

# Security Considerations

The database should:

* Restrict access through the application layer.
* Validate all incoming data before persistence.
* Avoid storing unnecessary sensitive information.
* Never expose raw database errors directly to users.

Version 1 does not encrypt the database file.

Future versions may introduce optional database encryption.

---

# Failure Recovery

If a write operation fails:

* Roll back the transaction.
* Preserve existing data.
* Log the error.
* Present a user-friendly message.

Data integrity always takes priority over completing an operation.

---

# Testing Requirements

Database testing should verify:

* CRUD operations.
* Transaction rollback.
* Constraint enforcement.
* Foreign key integrity.
* Migration correctness.
* Backup and restore workflows.

Tests should run against an isolated database.

---

# Acceptance Criteria

The database architecture is complete when:

* SQLite is configured correctly.
* Transactions are atomic.
* Constraints are enforced.
* Data integrity is preserved.
* Migrations are supported.
* Performance meets documented expectations.
* Backup and recovery procedures are documented.

---

# Future Considerations

Future versions may introduce:

* PostgreSQL support.
* Database encryption.
* Cloud synchronization.
* Conflict resolution.
* Multi-device replication.

These enhancements should extend the architecture without changing the local-first philosophy established in Version 1.

---

# References

* Architecture
* Technology Stack
* Schema
* Migrations
* Indexes

---

# Goal

The database should provide a dependable, predictable, and maintainable foundation for FinTrack.

Every feature in the application ultimately relies on the database being accurate, consistent, and resilient.
