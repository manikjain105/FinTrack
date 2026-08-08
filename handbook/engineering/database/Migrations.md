---
title: Database Migrations
category: Engineering
status: Approved
version: 1.0
owner: Engineering
depends_on:
  - Database
  - Database Schema
related:
  - Indexes
  - Data Models
---

# Database Migrations

> **Every schema change should be intentional, repeatable, and traceable.**

---

# Purpose

This document defines how database schema changes are created, reviewed, tested, and deployed.

Migrations ensure that every FinTrack database evolves in a predictable and reproducible manner.

No schema changes should occur outside the migration system.

---

# Philosophy

Database migrations are part of the application's source code.

Every schema modification must:

* Be version controlled.
* Be reviewed.
* Be testable.
* Be reproducible.
* Preserve user data whenever possible.

---

# Migration Tool

Version 1 uses:

| Component      | Technology |
| -------------- | ---------- |
| ORM            | SQLAlchemy |
| Migration Tool | Alembic    |

All schema evolution should be managed through Alembic.

---

# Migration Lifecycle

Every migration follows the same lifecycle.

```text
Design Change

↓

Update Schema.md

↓

Create Migration

↓

Review

↓

Run Tests

↓

Apply Migration
```

Documentation should always be updated before implementation.

---

# Migration Naming

Migration filenames should be descriptive.

Examples:

```text
001_initial_schema.py

002_add_budget_table.py

003_add_notes_to_transaction.py

004_create_indexes.py
```

Avoid generic names such as:

```text
update.py

fix.py

migration.py
```

---

# Versioning

Migration numbers are sequential.

Example:

```text
001

002

003

004
```

Numbers should never be reused.

---

# Upgrade Function

Every migration must implement an upgrade path.

Example responsibilities:

* Create tables.
* Add columns.
* Create indexes.
* Add constraints.

The upgrade should be idempotent when practical.

---

# Downgrade Function

Every migration should provide a downgrade path unless clearly documented otherwise.

Downgrades should:

* Remove newly created objects.
* Restore the previous schema.
* Preserve data where practical.

If a migration cannot be safely reversed, document the reason explicitly.

---

# Allowed Operations

Examples:

* Create table.
* Rename column.
* Add column.
* Add index.
* Add constraint.
* Modify constraint.

---

# Discouraged Operations

Avoid:

* Manual database edits.
* Direct production modifications.
* Data deletion without migration.
* Silent data transformations.

All structural changes should pass through the migration system.

---

# Migration Review Checklist

Before approving a migration, verify:

* Schema documentation updated.
* Naming follows convention.
* Upgrade tested.
* Downgrade tested.
* No unnecessary data loss.
* Constraints validated.

---

# Testing

Each migration should be tested against:

* Empty database.
* Existing populated database.
* Previous schema version.

Migration failures should be reproducible.

---

# Data Migrations

Schema migrations and data migrations should remain separate whenever possible.

Examples of data migrations:

* Renaming category values.
* Normalizing merchant names.
* Backfilling timestamps.

Data migrations should be documented and tested independently.

---

# Rollback Strategy

If a migration fails:

```text
Migration Started

↓

Failure

↓

Rollback

↓

Database Restored
```

The application should never continue with a partially migrated schema.

---

# Seed Data

Default records such as built-in categories should be inserted through controlled seed scripts or documented initialization routines rather than ad hoc SQL.

Seed operations should be repeatable.

---

# Production Rules

Production databases should:

* Run migrations in order.
* Never skip versions.
* Never modify historical migration files.
* Always back up data before applying new migrations.

---

# Development Rules

Developers may recreate local databases during active development.

Once a migration is committed:

* Do not rewrite its history.
* Create a new migration for subsequent changes.

---

# Error Handling

Migration failures should:

* Stop execution immediately.
* Preserve existing data.
* Produce clear diagnostic logs.
* Require explicit user action before retrying.

---

# Acceptance Criteria

The migration process is complete when:

* Every schema change has a migration.
* Migration order is deterministic.
* Upgrade and downgrade paths are documented.
* Migration testing is part of the development workflow.
* Historical migrations remain immutable.

---

# Future Considerations

Future versions may introduce:

* Automated migration validation.
* Continuous integration migration tests.
* Database compatibility checks.
* Multi-version upgrade support.

These enhancements should build upon the migration process defined here.

---

# Goal

The migration system should allow the FinTrack database to evolve safely over time without compromising data integrity or developer confidence.
