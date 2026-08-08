---
title: Parser Categorization
category: Engineering
status: Approved
version: 1.0
owner: Engineering
depends_on:
  - Parser
  - Parser Grammar
  - Database Schema
related:
  - Transactions API
  - Categories
---

# Parser Categorization

> **Categorization assigns each transaction to the most appropriate spending category.**

---

# Purpose

This document defines how the FinTrack parser determines the category of a transaction.

Version 1 uses a rule-based categorization system designed to be predictable, maintainable, and easy to extend.

---

# Responsibilities

The categorization process is responsible for:

* Matching user-provided categories.
* Inferring categories from merchant names.
* Applying default categories when no match is found.

Categorization should produce a single category for every valid transaction.

---

# Categorization Priority

Categories are assigned using the following order:

1. User-provided category
2. Merchant-based category
3. Default category

The first successful match is used.

---

# User-Provided Category

If the input contains a valid category:

```text
Pizza 650 Food
```

The parser assigns:

* Category: Food

No additional inference is performed.

---

# Merchant Matching

If no category is supplied, the parser checks whether the merchant matches a known category mapping.

Examples:

| Merchant | Category      |
| -------- | ------------- |
| Swiggy   | Food          |
| Zomato   | Food          |
| Uber     | Travel        |
| Ola      | Travel        |
| Amazon   | Shopping      |
| Netflix  | Entertainment |

Matching should be case-insensitive.

---

# Default Category

If no match is found:

```text
Stationery Shop 240
```

The parser assigns:

* Category: Other

This ensures every transaction has a valid category.

---

# Matching Rules

Merchant matching should:

* Ignore letter casing.
* Ignore leading and trailing whitespace.
* Prefer exact matches over partial matches.

Future versions may introduce more advanced matching strategies.

---

# Category Validation

Assigned categories must exist in the Category table.

If a supplied category does not exist:

* Return a validation error.

The parser should not create new categories automatically.

---

# Example Inputs

| Input               | Assigned Category |
| ------------------- | ----------------- |
| Swiggy 420          | Food              |
| Uber 300            | Travel            |
| Salary 75000 Income | Other*            |
| Amazon 2500         | Shopping          |
| Pizza 600 Food      | Food              |

* Income transactions may be assigned to a dedicated income category if supported by the application configuration.

---

# Unknown Merchants

Unknown merchants should not prevent successful parsing.

Instead:

* Assign the default category.
* Continue processing the transaction.

---

# Extensibility

Future versions may introduce:

* Merchant aliases
* Keyword matching
* User-defined merchant mappings
* AI-assisted categorization
* Learning from previous corrections

These enhancements should preserve deterministic behavior unless users explicitly enable adaptive categorization.

---

# Performance Expectations

Categorization should:

* Complete as part of the normal parsing process.
* Introduce minimal processing overhead.
* Scale efficiently as the merchant mapping list grows.

---

# Testing

Testing should verify:

* User-specified categories
* Merchant matching
* Default category assignment
* Invalid category handling
* Case-insensitive matching

---

# Acceptance Criteria

The categorization system is complete when:

* Categories are assigned according to the documented priority.
* Merchant mappings work consistently.
* Unknown merchants receive the default category.
* Invalid categories are rejected.
* Behavior remains deterministic.

---

# Goal

The categorization system should assign meaningful categories with minimal user effort while remaining predictable, transparent, and easy to maintain.
