---
title: Parser
category: Engineering
status: Approved
version: 1.0
owner: Engineering
depends_on:
  - Architecture
  - Transactions
  - Database Schema
related:
  - Grammar
  - Categorization
  - Transactions API
---

# Parser

> **The Parser transforms user input into structured transaction data.**

---

# Purpose

This document defines the architecture and processing pipeline of the FinTrack parser.

The parser is responsible for interpreting user input, extracting meaningful transaction information, validating the result, and producing a structured transaction that can be stored in the database.

The detailed parsing rules are documented in **Grammar.md**.

---

# Responsibilities

The Parser is responsible for:

* Processing natural-language transaction input
* Extracting transaction fields
* Performing basic validation
* Producing a structured transaction object

The Parser does **not**:

* Save data to the database
* Calculate budgets
* Generate analytics
* Apply business rules beyond parsing

Those responsibilities belong to the Service Layer.

---

# Processing Pipeline

Every input follows the same processing pipeline.

```text
User Input

↓

Normalize Input

↓

Parse Tokens

↓

Extract Fields

↓

Validate Result

↓

Structured Transaction
```

Each stage performs one well-defined responsibility.

---

# Input

The parser accepts free-form text entered by the user.

Examples:

* `Coffee 180`
* `Uber 420 travel`
* `Salary 75000 income`
* `Milk 65 groceries`

Supported input patterns are defined in **Grammar.md**.

---

# Output

The parser returns a structured transaction containing the fields it was able to identify.

Typical fields include:

* Amount
* Date
* Merchant
* Category
* Transaction Type
* Notes

Missing optional fields remain empty.

---

# Validation

Before returning a result, the parser validates:

* Amount exists
* Amount is positive
* Date format (if supplied)
* Transaction type (if supplied)

If validation fails, the parser returns a descriptive error rather than a partial transaction.

---

# Error Handling

Common parser errors include:

* Missing amount
* Invalid amount
* Unsupported date format
* Ambiguous input

Errors should be understandable and help users correct their input.

---

# Interaction with Other Components

The parser interacts with:

* Transactions API
* Service Layer
* Category data

It should remain independent of database persistence.

---

# Performance Expectations

The parser should:

* Process typical inputs almost instantly.
* Produce deterministic results.
* Scale efficiently as parsing rules expand.

The same input should always produce the same output.

---

# Extensibility

New parsing capabilities should be added by extending parsing rules rather than rewriting the parser.

Future enhancements may include:

* Relative dates
* Currency recognition
* Recurring transaction phrases
* Multi-language support

The parser architecture should support these additions without major restructuring.

---

# Testing

Testing should verify:

* Successful parsing
* Invalid input handling
* Validation failures
* Consistent output
* Edge cases

Parser tests should remain independent of database and API tests.

---

# Acceptance Criteria

The Parser is complete when:

* User input is converted into structured transaction data.
* Validation is performed consistently.
* Errors are reported clearly.
* Output follows the documented structure.
* The parser remains independent of persistence and business logic.

---

# Goal

The Parser should make transaction entry fast, forgiving, and predictable.

Users should be able to type naturally while consistently producing valid, structured financial records.
