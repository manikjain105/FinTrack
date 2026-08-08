---
title: Navigation Map
category: Product
status: Approved
version: 1.0
owner: Product
depends_on:
  - Dashboard
  - Design System
  - Application Shell
related:
  - Transactions
  - Budgets
  - Analytics
  - Settings
---

# Navigation Map

> **The Navigation Map defines how users move through FinTrack.**

---

# Purpose

This document specifies the relationships between product features and the expected navigation flow throughout the application.

It answers:

* Where can users go?
* How do they get there?
* What is the fastest path?
* Which screen owns each workflow?

Navigation should always feel predictable.

---

# Product Structure

Version 1 consists of five primary destinations.

```text
Dashboard

Transactions

Budgets

Analytics

Settings
```

Every feature should be reachable within two interactions.

---

# Application Map

```text
Dashboard
│
├── Transactions
│
├── Budgets
│
├── Analytics
│
└── Settings
```

Dashboard is the primary entry point.

All major workflows begin or return here.

---

# Primary Navigation

The Application Shell exposes these destinations.

| Destination  | Purpose                      |
| ------------ | ---------------------------- |
| Dashboard    | Financial overview           |
| Transactions | Complete transaction history |
| Budgets      | Budget management            |
| Analytics    | Spending analysis            |
| Settings     | Application preferences      |

The order should remain stable across all platforms.

---

# Screen Relationships

## Dashboard

Primary destination.

Links to:

* Transactions
* Analytics
* Budgets

---

## Transactions

Users may:

* View all transactions.
* Search.
* Filter.
* Edit.
* Delete.

Returns naturally to Dashboard.

---

## Budgets

Users may:

* Create budgets.
* Modify budgets.
* Review budget performance.

Budget summaries are reflected on Dashboard.

---

## Analytics

Provides detailed exploration of spending.

Users may:

* Change time periods.
* Compare months.
* Drill into categories.

Analytics should never replace the Dashboard.

---

## Settings

Contains:

* Currency
* Theme
* Categories
* Import & Export
* Preferences

Settings should never interrupt financial workflows.

---

# Common User Journeys

## Record an Expense

```text
Dashboard

↓

Command Palette

↓

Transaction Saved

↓

Dashboard Updated
```

No navigation required.

---

## Review Spending

```text
Dashboard

↓

Analytics

↓

Dashboard
```

---

## Edit a Transaction

```text
Dashboard

↓

Transactions

↓

Edit

↓

Save

↓

Transactions
```

---

## Configure Monthly Budget

```text
Dashboard

↓

Budgets

↓

Save Budget

↓

Dashboard
```

---

## Export Data

```text
Dashboard

↓

Settings

↓

Export

↓

Download
```

---

# Cross-Screen Updates

Some actions affect multiple screens immediately.

| Action             | Updates                                     |
| ------------------ | ------------------------------------------- |
| Add Transaction    | Dashboard, Transactions, Budgets, Analytics |
| Edit Transaction   | Dashboard, Transactions, Budgets, Analytics |
| Delete Transaction | Dashboard, Transactions, Budgets, Analytics |
| Change Budget      | Dashboard, Budgets                          |
| Change Settings    | Entire application where applicable         |

Users should never need to manually refresh data.

---

# Deep Linking

Future versions should support direct navigation to:

* A specific month.
* A category.
* A transaction.
* An analytics view.

Version 1 does not require shareable URLs but should avoid architecture that prevents them.

---

# Back Navigation

Users should always be able to return to their previous context.

Examples:

* Preserve filters.
* Preserve selected month.
* Preserve table pagination.
* Preserve scroll position where appropriate.

---

# Unsaved Changes

If users attempt to leave a screen with unsaved changes:

* Warn the user.
* Allow Save.
* Allow Discard.
* Allow Cancel.

This applies only to editable forms.

---

# Mobile Navigation

Primary destinations are available through the Bottom Navigation Bar.

The same information architecture should be preserved across desktop and mobile.

---

# Keyboard Navigation

Users should be able to navigate efficiently without a mouse.

Recommended shortcuts:

| Shortcut     | Action          |
| ------------ | --------------- |
| Ctrl/Cmd + K | Command Palette |
| G D          | Dashboard       |
| G T          | Transactions    |
| G B          | Budgets         |
| G A          | Analytics       |
| G S          | Settings        |

---

# Navigation Principles

Navigation should:

* Minimize clicks.
* Preserve context.
* Avoid dead ends.
* Avoid duplicate routes.
* Maintain consistent terminology.

Users should always know where they are and where they can go next.

---

# Accessibility

Navigation flows should support:

* Keyboard-only users.
* Screen readers.
* Visible focus indicators.
* Logical reading order.

Every route should remain fully accessible without requiring a pointing device.

---

# Acceptance Criteria

The Navigation Map is complete when:

* Every primary feature is reachable from the Application Shell.
* Major user journeys are documented.
* Cross-screen updates are defined.
* Navigation behavior is consistent across desktop and mobile.
* No feature becomes inaccessible through normal use.

---

# Future Enhancements

Future versions may introduce:

* Global search navigation.
* Recently visited screens.
* Favorite destinations.
* Workspace support.
* Keyboard command navigation.

These enhancements should extend the existing navigation model without changing the core information architecture.

---

# Goal

Users should never wonder:

*"Where do I go next?"*

Navigation should feel so natural that it becomes invisible, allowing users to focus entirely on managing their finances.
