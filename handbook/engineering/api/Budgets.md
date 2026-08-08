---
title: Budgets API
category: Engineering
status: Approved
version: 1.0
owner: Engineering
depends_on:
  - API Overview
  - Database Schema
  - Budgets
related:
  - Transactions API
  - Dashboard API
  - Analytics API
---

# Budgets API

> **The Budgets API manages budget creation, retrieval, updates, and budget performance information.**

---

# Purpose

This document defines the API endpoints responsible for budget management.

The Budgets API enables the frontend to create, update, retrieve, and delete budgets while providing budget progress information used throughout the application.

All endpoints follow the standards defined in **API-Overview.md**.

---

# Base Endpoint

```text
/api/v1/budgets
```

---

# Responsibilities

The Budgets API is responsible for:

* Creating budgets
* Listing budgets
* Retrieving individual budgets
* Updating budgets
* Deleting budgets
* Returning budget progress

Business logic such as calculating spending against budgets is handled by the Service Layer.

---

# Endpoints

| Method | Endpoint            | Purpose                  |
| ------ | ------------------- | ------------------------ |
| GET    | `/budgets`          | List budgets             |
| GET    | `/budgets/{id}`     | Retrieve a budget        |
| POST   | `/budgets`          | Create a budget          |
| PUT    | `/budgets/{id}`     | Update a budget          |
| DELETE | `/budgets/{id}`     | Delete a budget          |
| GET    | `/budgets/progress` | Retrieve budget progress |

---

# List Budgets

Returns all budgets for the selected period.

### Query Parameters

| Parameter | Required | Description            |
| --------- | -------- | ---------------------- |
| month     | No       | Budget month (YYYY-MM) |
| category  | No       | Filter by category     |

If no month is specified, the current month is used.

---

# Create Budget

### Required Fields

* Month
* Budget Amount

### Optional Fields

* Category

If no category is provided, the budget represents the overall monthly budget.

---

# Retrieve Budget

Returns the details of a single budget using its unique identifier.

If the budget does not exist:

* Return **404 Not Found**.

---

# Update Budget

Allows modification of an existing budget.

Updates should:

* Validate incoming data.
* Preserve the budget identifier.
* Update the `updated_at` timestamp.

---

# Delete Budget

Deletes the selected budget.

Deleting a budget should not modify any transactions.

Budget progress should be recalculated automatically after deletion.

---

# Budget Progress

Returns the current status of one or more budgets.

Typical values include:

* Budget Amount
* Amount Spent
* Remaining Budget
* Percentage Used
* Budget Status (On Track, Near Limit, Exceeded)

Progress calculations are performed by the Service Layer.

---

# Response Behavior

Successful responses follow the standard response format defined in **API-Overview.md**.

Budget progress should always reflect the latest transaction data.

---

# Validation

Incoming requests should validate:

* Valid month format
* Positive budget amount
* Valid category identifier (if provided)

Invalid requests must not modify stored data.

---

# Performance Expectations

The Budgets API should:

* Return budget information efficiently.
* Support month and category filtering.
* Recalculate budget progress with minimal overhead.

Database indexes should be used where appropriate.

---

# Error Scenarios

Common errors include:

| Status | Scenario                |
| ------ | ----------------------- |
| 400    | Invalid request         |
| 404    | Budget not found        |
| 422    | Validation failed       |
| 500    | Unexpected server error |

---

# Relationship to Other Features

The Budgets API interacts with:

* Transactions
* Dashboard
* Analytics
* Reports

Budget calculations should remain centralized in the Service Layer to ensure consistency across all features.

---

# Testing

Testing should verify:

* CRUD operations
* Budget progress calculations
* Filtering
* Validation
* Error handling

---

# Acceptance Criteria

The Budgets API is complete when:

* All CRUD endpoints are implemented.
* Budget progress is calculated correctly.
* Responses follow the standard API format.
* Validation rules are enforced.
* Related application data updates correctly.

---

# Goal

The Budgets API should provide a reliable interface for managing spending limits while delivering accurate and consistent budget information across the application.
