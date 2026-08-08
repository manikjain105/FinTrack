---
title: API Overview
category: Engineering
status: Approved
version: 1.0
owner: Engineering
depends_on:
  - API Engineering
  - Architecture
  - Database
related:
  - Transactions
  - Dashboard
  - Budgets
  - Analytics
  - Reports
---

# API Overview

> **The API is the contract between the FinTrack frontend and backend.**

---

# Purpose

This document defines the standards, conventions, and contracts that every API endpoint must follow.

It ensures consistency across all API implementations and provides a common foundation for endpoint-specific documentation.

---

# Version

Current API version:

```text
v1
```

Base URL:

```text
/api/v1
```

Future breaking changes must be introduced through a new version.

---

# Architecture

Version 1 follows a synchronous request-response model.

```text
Frontend
      │
      ▼
FastAPI Router
      │
      ▼
Service Layer
      │
      ▼
Repository Layer
      │
      ▼
SQLite
```

Business logic belongs exclusively in the Service Layer.

---

# Endpoint Naming

Use resource-oriented URLs.

Examples:

```text
GET    /transactions
GET    /transactions/{id}

POST   /transactions

PUT    /transactions/{id}

DELETE /transactions/{id}
```

Avoid verbs in endpoint names.

Good:

```text
POST /transactions
```

Avoid:

```text
POST /createTransaction
```

---

# HTTP Methods

| Method | Purpose                    |
| ------ | -------------------------- |
| GET    | Retrieve data              |
| POST   | Create resources           |
| PUT    | Replace existing resources |
| PATCH  | Partial update (future)    |
| DELETE | Remove resources           |

Version 1 uses GET, POST, PUT, and DELETE.

---

# Request Format

All request bodies use JSON.

Example:

```json
{
  "amount": 180,
  "merchant": "Starbucks",
  "category_id": "cat_food",
  "type": "Expense",
  "date": "2026-07-09"
}
```

Dates use ISO-8601 format.

Currency symbols should never be included in numeric values.

---

# Standard Success Response

Every successful response follows the same structure.

```json
{
  "success": true,
  "data": {},
  "message": null
}
```

`data` contains the requested resource or collection.

---

# Standard Error Response

Every failed request follows the same structure.

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Amount must be greater than zero."
  }
}
```

Clients should rely on `code` for programmatic handling and `message` for user-facing feedback where appropriate.

---

# HTTP Status Codes

| Status | Meaning               |
| ------ | --------------------- |
| 200    | Success               |
| 201    | Resource Created      |
| 204    | No Content            |
| 400    | Invalid Request       |
| 404    | Resource Not Found    |
| 409    | Conflict              |
| 422    | Validation Error      |
| 500    | Internal Server Error |

Use the most specific applicable status code.

---

# Validation

Every request must be validated before reaching the Service Layer.

Validation includes:

* Required fields
* Data types
* Numeric ranges
* Enum values
* Date formats

Invalid requests should never modify application state.

---

# Pagination

Collection endpoints support pagination.

Query parameters:

```text
?page=1
&page_size=25
```

Default page size:

```text
25
```

Maximum page size:

```text
100
```

Paginated response:

```json
{
  "success": true,
  "data": {
    "items": [],
    "page": 1,
    "page_size": 25,
    "total_items": 240,
    "total_pages": 10
  }
}
```

---

# Filtering

Filtering uses query parameters.

Example:

```text
GET /transactions?category=Food&type=Expense
```

Multiple filters combine using logical AND.

---

# Sorting

Sorting uses query parameters.

Example:

```text
GET /transactions?sort=date&order=desc
```

Allowed order values:

* asc
* desc

---

# Date & Time

All timestamps:

* Stored in UTC.
* Returned in ISO-8601 format.

Example:

```text
2026-07-09T14:30:00Z
```

Date-only values use:

```text
YYYY-MM-DD
```

---

# Decimal Values

Monetary values are represented as JSON numbers.

Example:

```json
{
  "amount": 180.50
}
```

The frontend is responsible for formatting currency according to user preferences.

---

# Idempotency

Safe methods:

* GET

Idempotent methods:

* PUT
* DELETE

POST is not idempotent.

Clients should avoid retrying POST requests automatically without appropriate safeguards.

---

# Error Codes

Standard application error codes:

| Code               | Description             |
| ------------------ | ----------------------- |
| VALIDATION_ERROR   | Invalid request data    |
| NOT_FOUND          | Resource does not exist |
| DUPLICATE_RESOURCE | Resource already exists |
| DATABASE_ERROR     | Persistence failure     |
| INTERNAL_ERROR     | Unexpected failure      |

Endpoint-specific documents may define additional codes where necessary.

---

# Authentication

Version 1 does not require authentication.

The API assumes a single-user local application.

Future versions may introduce authentication without changing existing resource semantics.

---

# Logging

Every request should record:

* Timestamp
* HTTP method
* Endpoint
* Response status
* Processing time

Sensitive request data must not be logged.

---

# API Stability

Version 1 guarantees:

* Stable endpoint names
* Stable response formats
* Backward-compatible changes only

Breaking changes require a new API version.

---

# Acceptance Criteria

The API contract is complete when:

* Every endpoint follows the documented conventions.
* Requests and responses are consistent.
* Validation occurs before business logic.
* Status codes are used correctly.
* Pagination, filtering, and sorting behave consistently.

---

# Future Considerations

Future versions may introduce:

* PATCH support
* Authentication
* API keys
* Rate limiting
* Webhooks
* Streaming endpoints

These enhancements should extend the API while preserving the design principles established in Version 1.

---

# Goal

The API should be predictable, consistent, and easy to consume.

A frontend developer—or AI coding agent—should be able to integrate with any FinTrack endpoint without reading the backend implementation.
