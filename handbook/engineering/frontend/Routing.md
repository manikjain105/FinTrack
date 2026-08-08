---
title: Routing
category: Engineering
status: Approved
version: 1.0
owner: Engineering
depends_on:
  - Frontend Engineering
  - Navigation Map
  - State Management
related:
  - Dashboard
  - Transactions
  - Budgets
  - Analytics
  - Reports
---

# Routing

> **Routing should make navigation predictable, intuitive, and aligned with the product structure.**

---

# Purpose

This document defines the routing strategy for the FinTrack frontend.

It establishes how users navigate between screens, how routes are organized, and the conventions followed when adding new pages.

---

# Routing Philosophy

Version 1 uses a straightforward, page-based routing structure.

Each primary feature has a dedicated route.

Routes should represent meaningful user destinations rather than individual UI components.

---

# Route Structure

| Route           | Feature      |
| --------------- | ------------ |
| `/`             | Dashboard    |
| `/transactions` | Transactions |
| `/budgets`      | Budgets      |
| `/analytics`    | Analytics    |
| `/reports`      | Reports      |
| `/settings`     | Settings     |

Future routes should follow the same naming convention.

---

# Navigation Flow

Users can navigate directly between all primary sections.

```text
Dashboard

├── Transactions

├── Budgets

├── Analytics

├── Reports

└── Settings
```

Navigation structure should remain consistent throughout the application.

---

# Route Responsibilities

Each route is responsible for:

* Loading the required data.
* Rendering the appropriate page.
* Managing page-specific UI state.
* Coordinating interactions with shared components.

Business logic should remain outside the routing layer.

---

# URL Conventions

Routes should:

* Use lowercase.
* Use hyphens where multiple words are required.
* Avoid implementation details.

Examples:

```text
/monthly-report

/import-history
```

Avoid:

```text
/MonthlyReport

/reportPage
```

---

# Route Parameters

Version 1 uses route parameters only where required.

Examples:

```text
/transactions/:id
```

Parameters should represent stable resource identifiers.

---

# Query Parameters

Query parameters are used for temporary view state such as:

* Filtering
* Sorting
* Pagination

Example:

```text
/transactions?page=2&sort=date&order=desc
```

Query parameters should not represent permanent application state.

---

# Unknown Routes

Unknown routes should display a friendly "Page Not Found" screen.

The page should:

* Explain that the requested page could not be found.
* Provide navigation back to the Dashboard.

---

# Future Routing

Future versions may introduce routes for:

* Onboarding
* Import Wizard
* Export History
* Help
* User Profile

These additions should follow the established routing conventions.

---

# Performance Considerations

Routing should:

* Load pages efficiently.
* Preserve application responsiveness.
* Support code splitting where appropriate.

Navigation should feel immediate for typical user interactions.

---

# Testing

Testing should verify:

* Route accessibility.
* Navigation behavior.
* Route parameter handling.
* Query parameter handling.
* Unknown route handling.

---

# Acceptance Criteria

Routing is complete when:

* Every primary feature has a documented route.
* URL conventions are followed consistently.
* Navigation matches the Product Handbook.
* Unknown routes are handled gracefully.
* Routing remains independent of business logic.

---

# Goal

The routing strategy should provide a clear, maintainable navigation structure that reflects the application's features while remaining simple to extend as FinTrack grows.
