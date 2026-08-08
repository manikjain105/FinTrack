---
title: Parser Grammar
category: Engineering
status: Approved
version: 1.0
owner: Engineering
depends_on:
  - Parser
related:
  - Categorization
  - Transactions API
---

# Parser Grammar

> **The grammar defines the input patterns that FinTrack can interpret.**

---

# Purpose

This document defines the supported input formats for the FinTrack parser.

The grammar is designed to be flexible enough for natural typing while remaining predictable and deterministic.

The parser should interpret common transaction patterns consistently.

---

# Design Principles

The grammar should be:

* Simple
* Predictable
* Order-tolerant where practical
* Easy to extend

When multiple interpretations are possible, the parser should choose the most consistent result.

---

# Supported Fields

The parser recognizes the following transaction fields:

* Amount
* Merchant
* Category
* Transaction Type
* Date
* Notes

Not every input must contain every field.

---

# Basic Pattern

The most common input format is:

```text
<merchant> <amount>
```

Examples:

```text
Coffee 180

Uber 420

Milk 65
```

---

# Category Pattern

Users may include a category.

Pattern:

```text
<merchant> <amount> <category>
```

Examples:

```text
Pizza 650 Food

Bus 40 Travel

Book 900 Education
```

If the category is omitted, the parser attempts automatic categorization.

---

# Transaction Type Pattern

Users may specify the transaction type.

Pattern:

```text
<merchant> <amount> <type>
```

Examples:

```text
Salary 75000 Income

Freelance 12000 Income

Coffee 180 Expense
```

If no type is provided, **Expense** is assumed.

---

# Date Pattern

Users may include an explicit date.

Pattern:

```text
<merchant> <amount> <date>
```

Examples:

```text
Coffee 180 2026-07-09

Taxi 350 2026-07-08
```

If no date is provided, the current date is used.

---

# Notes Pattern

Additional words not recognized as structured fields are treated as notes.

Example:

```text
Coffee 180 with client
```

Result:

* Merchant: Coffee
* Amount: 180
* Notes: with client

---

# Flexible Ordering

Where practical, field order should not be strictly enforced.

Examples:

```text
180 Coffee

Travel Uber 420

Income Salary 75000
```

The parser should identify fields based on meaning rather than position whenever possible.

---

# Amount Rules

Amounts must:

* Be numeric
* Be greater than zero

Examples:

Valid:

```text
180

99.50

1200
```

Invalid:

```text
-50

abc
```

---

# Category Rules

Categories should match existing category names.

Matching should be case-insensitive.

Unknown categories are handled by the categorization logic.

---

# Date Rules

Version 1 supports:

```text
YYYY-MM-DD
```

Future versions may introduce relative dates such as:

* Today
* Yesterday
* Last Friday

---

# Validation

The parser requires:

* A valid amount

Optional fields may be omitted.

Inputs missing a valid amount should return a validation error.

---

# Unsupported Patterns

Version 1 does not support:

* Multiple transactions in one input
* Currency conversion
* Split transactions
* Mathematical expressions

These may be introduced in future versions.

---

# Examples

| Input                 | Parsed Result            |
| --------------------- | ------------------------ |
| Coffee 180            | Expense transaction      |
| Salary 75000 Income   | Income transaction       |
| Uber 420 Travel       | Expense with category    |
| Book 900 Education    | Expense with category    |
| Coffee 180 2026-07-09 | Expense with custom date |

---

# Extensibility

Future grammar enhancements may include:

* Relative dates
* Currency symbols
* Recurring transaction phrases
* Natural language amounts
* Multiple language support

New grammar rules should remain backward compatible whenever practical.

---

# Testing

Testing should verify:

* Supported patterns
* Optional field handling
* Flexible ordering
* Validation failures
* Unsupported inputs

---

# Acceptance Criteria

The grammar is complete when:

* Supported input patterns are documented.
* Validation rules are defined.
* Examples cover common usage.
* Unsupported patterns are identified.
* Parser behavior remains deterministic.

---

# Goal

The grammar should allow users to enter transactions naturally while ensuring that every supported input is interpreted consistently and predictably.
