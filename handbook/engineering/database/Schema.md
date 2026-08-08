---
title: Database Schema
category: Engineering
status: Approved
version: 1.0
owner: Engineering
depends_on:
  - Database
  - Architecture
related:
  - Migrations
  - Indexes
  - Data Models
---

# Database Schema

> **The schema defines the persistent data model of FinTrack.**

---

# Purpose

This document specifies every table, column, relationship, constraint, and index used by FinTrack Version 1.

This document is the authoritative source for the database structure.

Business logic belongs in the Service Layer and is intentionally excluded from this specification.

---

# Schema Overview

Version 1 consists of four primary tables.

```text
Categories
      │
      │
      ▼
Transactions
      │
      ▼
Budgets

UserPreferences
```

Each table has a single responsibility.

---

# Naming Conventions

## Tables

* Singular nouns
* PascalCase

Examples:

```text
Transaction
Budget
Category
UserPreference
```

---

## Columns

* snake_case
* lowercase

Examples:

```text
created_at

updated_at

category_id
```

---

# Table: Category

## Purpose

Stores transaction categories.

---

### Columns

| Column     | Type      | Nullable | Default           | Description        |
| ---------- | --------- | -------- | ----------------- | ------------------ |
| id         | UUID      | No       | Generated         | Primary Key        |
| name       | TEXT      | No       | —                 | Category name      |
| icon       | TEXT      | Yes      | NULL              | Icon identifier    |
| color      | TEXT      | Yes      | NULL              | Theme color token  |
| is_default | BOOLEAN   | No       | TRUE              | System category    |
| created_at | TIMESTAMP | No       | CURRENT_TIMESTAMP | Creation timestamp |
| updated_at | TIMESTAMP | No       | CURRENT_TIMESTAMP | Last modification  |

---

### Constraints

Primary Key

```sql
PRIMARY KEY(id)
```

Unique

```sql
UNIQUE(name)
```

---

### Relationships

One Category

↓

Many Transactions

---

# Table: Transaction

## Purpose

Stores every financial transaction.

---

### Columns

| Column      | Type          | Nullable | Default           | Description        |
| ----------- | ------------- | -------- | ----------------- | ------------------ |
| id          | UUID          | No       | Generated         | Primary Key        |
| date        | DATE          | No       | —                 | Transaction date   |
| amount      | DECIMAL(12,2) | No       | —                 | Transaction amount |
| type        | TEXT          | No       | Expense           | Income / Expense   |
| merchant    | TEXT          | Yes      | NULL              | Merchant           |
| notes       | TEXT          | Yes      | NULL              | User notes         |
| category_id | UUID          | No       | —                 | FK → Category      |
| created_at  | TIMESTAMP     | No       | CURRENT_TIMESTAMP | Creation timestamp |
| updated_at  | TIMESTAMP     | No       | CURRENT_TIMESTAMP | Last modification  |

---

### Constraints

Primary Key

```sql
PRIMARY KEY(id)
```

Foreign Key

```sql
FOREIGN KEY(category_id)
REFERENCES Category(id)
ON DELETE RESTRICT
```

Check

```sql
amount > 0
```

Check

```sql
type IN ('Income','Expense')
```

---

### Relationships

Many Transactions

↓

One Category

---

# Table: Budget

## Purpose

Stores monthly and category budgets.

---

### Columns

| Column      | Type          | Nullable | Default           | Description              |
| ----------- | ------------- | -------- | ----------------- | ------------------------ |
| id          | UUID          | No       | Generated         | Primary Key              |
| month       | TEXT          | No       | —                 | YYYY-MM                  |
| category_id | UUID          | Yes      | NULL              | Optional category budget |
| amount      | DECIMAL(12,2) | No       | —                 | Budget value             |
| created_at  | TIMESTAMP     | No       | CURRENT_TIMESTAMP | Creation timestamp       |
| updated_at  | TIMESTAMP     | No       | CURRENT_TIMESTAMP | Last modification        |

---

### Constraints

Primary Key

```sql
PRIMARY KEY(id)
```

Foreign Key

```sql
FOREIGN KEY(category_id)
REFERENCES Category(id)
```

Check

```sql
amount > 0
```

---

### Relationships

One Budget

↓

Optional Category

---

# Table: UserPreference

## Purpose

Stores application preferences.

---

### Columns

| Column     | Type      | Nullable | Default           | Description      |
| ---------- | --------- | -------- | ----------------- | ---------------- |
| key        | TEXT      | No       | —                 | Preference key   |
| value      | TEXT      | No       | —                 | Preference value |
| updated_at | TIMESTAMP | No       | CURRENT_TIMESTAMP | Last update      |

---

### Constraints

Primary Key

```sql
PRIMARY KEY(key)
```

---

# Entity Relationship Diagram

```text
Category
───────────────
id
name
│
│
├──────────────┐
│              │
▼              ▼

Transaction    Budget

category_id    category_id
```

---

# Default Categories

Version 1 seeds the following categories.

* Food
* Travel
* Groceries
* Rent
* Bills
* Health
* Shopping
* Entertainment
* Investments
* Education
* Other

These records are created during initial database setup.

---

# Cascade Rules

| Parent   | Child       | Delete Behaviour |
| -------- | ----------- | ---------------- |
| Category | Transaction | Restrict         |
| Category | Budget      | Restrict         |

Deleting a category in use is not permitted.

---

# Data Types

Version 1 uses the following standard types.

| Logical Type | SQLite Representation |
| ------------ | --------------------- |
| UUID         | TEXT                  |
| Date         | TEXT (ISO-8601)       |
| Timestamp    | TEXT (ISO-8601 UTC)   |
| Boolean      | INTEGER               |
| Decimal      | NUMERIC               |
| Text         | TEXT                  |

Dates should always use ISO-8601 formatting.

---

# Example Transaction

```json
{
  "id": "2bdfc0f7-ef74-4fd0-b4ea-725f36f9d5b4",
  "date": "2026-07-09",
  "amount": 180.00,
  "type": "Expense",
  "merchant": "Starbucks",
  "category_id": "4c3d8baf...",
  "notes": "Coffee",
  "created_at": "2026-07-09T10:45:00Z",
  "updated_at": "2026-07-09T10:45:00Z"
}
```

---

# Versioning

Schema changes must occur only through documented migrations.

Tables should never be modified manually in production databases.

---

# Acceptance Criteria

The schema is complete when:

* Every table is defined.
* Every column has a documented type.
* Constraints are specified.
* Relationships are documented.
* Default seed data is identified.
* Example records are provided.

---

# Goal

The schema should describe the database so precisely that an engineer can implement it without making structural design decisions.
