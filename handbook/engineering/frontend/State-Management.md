---
title: State Management
category: Engineering
status: Approved
version: 1.0
owner: Engineering
depends_on:
  - Frontend Engineering
  - Architecture
  - Technology Stack
related:
  - Routing
  - API Overview
---

# State Management

> **Application state should have a single, well-defined owner.**

---

# Purpose

This document defines how application state is managed within the FinTrack frontend.

The goal is to ensure state remains predictable, maintainable, and easy to reason about as the application grows.

---

# State Management Philosophy

State should exist only where it is needed.

Prefer:

* Local component state for UI interactions.
* Global state for shared application data.
* Server data fetched through the API rather than duplicated locally.

Avoid storing derived data whenever it can be calculated from existing state.

---

# State Categories

FinTrack uses three categories of state.

## Local State

Local state belongs to an individual component.

Examples:

* Modal visibility
* Form input values
* Dropdown selection
* Loading indicators

Local state should not be shared between unrelated components.

---

## Global State

Global state is shared across multiple parts of the application.

Examples:

* Current month
* Theme
* User preferences
* Active filters

Global state should remain minimal.

---

## Server State

Server state originates from the backend.

Examples:

* Transactions
* Budgets
* Dashboard data
* Analytics
* Reports

The frontend should treat the backend as the source of truth for this data.

---

# State Ownership

Every piece of state should have a single owner.

Ownership determines:

* Who creates the state.
* Who updates the state.
* Who consumes the state.

Duplicating ownership leads to inconsistent behavior.

---

# Data Flow

State updates follow a predictable flow.

```text
User Action

↓

Frontend

↓

API Request

↓

Backend

↓

Updated Response

↓

Frontend State
```

Application state should always reflect the latest confirmed backend response.

---

# Derived State

Derived values should not be stored unless there is a measurable performance benefit.

Examples of derived state:

* Total expenses
* Remaining budget
* Transaction count

These values should be computed from existing data whenever practical.

---

# Persistence

Only selected application preferences should persist between sessions.

Examples:

* Theme
* Last selected month
* Display preferences

Temporary UI state should not be persisted.

---

# State Updates

State updates should be:

* Predictable
* Minimal
* Immutable
* Easy to trace

Avoid modifying existing state directly.

---

# Error Handling

Failed API requests should:

* Preserve existing state.
* Display an appropriate error message.
* Allow the user to retry the action.

Partial state updates should be avoided.

---

# Performance Considerations

State management should:

* Minimize unnecessary re-renders.
* Avoid duplicate API requests.
* Reuse existing data where appropriate.

Optimize only when performance measurements justify additional complexity.

---

# Testing

Testing should verify:

* State initialization
* State updates
* Error handling
* Persistence behavior
* Derived state calculations

State logic should be testable independently of the user interface.

---

# Acceptance Criteria

State management is complete when:

* State ownership is clearly defined.
* Local, global, and server state are used appropriately.
* Updates are predictable.
* Persistence is limited to required data.
* Components remain loosely coupled.

---

# Goal

The state management strategy should make FinTrack predictable to develop, easy to debug, and scalable as new features are added.
