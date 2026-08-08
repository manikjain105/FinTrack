---
title: Transactions
category: Product
status: Approved
version: 1.0
owner: Product
depends_on:
  - Dashboard
  - Navigation Map
  - Command Palette
  - Tables
  - Toasts
  - Modals
related:
  - Budgets
  - Analytics
  - Search
---

# Transactions

> **Transactions are the foundation of every financial insight in FinTrack.**

---

# Purpose

The Transactions feature provides a complete, searchable, and editable history of all financial activity.

It serves as the source of truth for every calculation performed throughout the application.

Every dashboard metric, chart, budget, and insight ultimately derives from transaction data.

---

# User Goals

Users visit the Transactions feature to:

* Review spending history.
* Search for a purchase.
* Correct mistakes.
* Delete incorrect entries.
* Filter spending.
* Verify financial records.

The page should prioritize speed and clarity over visual complexity.

---

# Screen Layout

```text
┌────────────────────────────────────────────────────────────────────────────┐
│ Transactions                                               July 2026 ▼     │
├────────────────────────────────────────────────────────────────────────────┤
│ Search...                                             + Add Transaction    │
├────────────────────────────────────────────────────────────────────────────┤
│ Filters: Category • Type • Date • Amount • Merchant                      │
├────────────────────────────────────────────────────────────────────────────┤
│ Transaction Table                                                   Sort ▼ │
├────────────────────────────────────────────────────────────────────────────┤
│ Pagination / Total Transactions                                         │
└────────────────────────────────────────────────────────────────────────────┘
```

---

# Primary Components

The Transactions screen consists of:

| Component         | Required |
| ----------------- | -------- |
| Search            | Yes      |
| Filter Bar        | Yes      |
| Transaction Table | Yes      |
| Pagination        | Yes      |
| Add Transaction   | Yes      |

---

# Transaction Model

Every transaction contains:

| Field                   | Required |
| ----------------------- | -------- |
| Date                    | Yes      |
| Amount                  | Yes      |
| Type (Income / Expense) | Yes      |
| Category                | Yes      |
| Merchant                | Yes      |
| Notes                   | Optional |
| Created At              | Yes      |
| Updated At              | Yes      |

Each transaction should have a unique identifier.

---

# Creating Transactions

Version 1 supports two methods.

## Method 1 — Command Palette

Preferred method.

Example:

```text
coffee 180

uber 240

salary 75000
```

The parser should automatically determine:

* Amount
* Category
* Type
* Merchant (where possible)

---

## Method 2 — Manual Form

Users may manually enter transaction details.

Required fields:

* Amount
* Category
* Date

Optional:

* Merchant
* Notes

---

# Editing Transactions

Users can edit:

* Date
* Amount
* Category
* Merchant
* Notes

Editing should immediately update:

* Dashboard
* Budgets
* Analytics
* Insights

No manual refresh should be required.

---

# Deleting Transactions

Deletion requires confirmation.

After deletion:

* Dashboard updates.
* Charts update.
* Budgets update.
* Insights update.

Display a toast with:

**Undo**

---

# Search

Search operates in real time.

Supported fields:

* Merchant
* Notes
* Category

Search should be case-insensitive.

---

# Filtering

Users can filter by:

* Month
* Date range
* Category
* Type
* Amount
* Merchant

Filters should combine logically.

---

# Sorting

Supported sorting:

* Date
* Amount
* Merchant
* Category

Default:

Newest first.

---

# Categories

Version 1 categories:

* Food
* Travel
* Groceries
* Rent
* Bills
* Clothes
* Health
* Education
* Investments
* Luxuries
* Other

Categories are configurable through Settings.

---

# Validation

Amount:

* Must be greater than zero.

Date:

* Cannot be invalid.

Category:

* Required.

Income:

* Cannot have negative values.

Validation errors should appear inline.

---

# Business Rules

* Editing a transaction recalculates all dependent metrics.
* Deleted transactions are removed from all calculations.
* Transactions belong to exactly one month.
* Categories should remain editable.
* Income and expenses are stored independently.

---

# Empty State

Display:

```text
No transactions yet.

Use the Command Palette or
click "Add Transaction"
to record your first expense.
```

---

# Loading State

Display:

* Table skeleton.
* Search placeholder.
* Filter placeholder.

Maintain layout throughout loading.

---

# Error State

Display:

```text
Unable to load transactions.

Please try again.
```

Preserve filters and search query where possible.

---

# Keyboard Shortcuts

| Shortcut     | Action                      |
| ------------ | --------------------------- |
| Ctrl/Cmd + K | Command Palette             |
| Ctrl/Cmd + F | Focus Search                |
| Delete       | Delete selected transaction |
| Esc          | Clear selection             |

---

# Performance Expectations

The Transactions page should:

* Open in under two seconds.
* Handle at least 10,000 transactions smoothly.
* Filter instantly for typical datasets.
* Preserve scroll position during edits.

---

# Accessibility

The Transactions feature must:

* Support full keyboard navigation.
* Use semantic table markup.
* Announce updates after edits and deletions.
* Maintain accessible focus order.

---

# Acceptance Criteria

The Transactions feature is complete when:

* Users can create, edit, and delete transactions.
* Search and filters work together.
* All dependent screens update automatically.
* Empty, loading, and error states are implemented.
* Accessibility requirements are satisfied.

---

# Future Enhancements

Future versions may introduce:

* Recurring transactions.
* Transaction attachments.
* Receipt scanning.
* Split transactions.
* Bulk editing.
* Smart merchant recognition.
* Duplicate detection.

These features should build upon the existing transaction model without changing its core structure.

---

# Goal

The Transactions feature should become the definitive record of a user's financial activity.

Every transaction should be easy to find, easy to edit, and immediately reflected throughout FinTrack.
