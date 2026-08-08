---
title: Budgets
category: Product
status: Approved
version: 1.0
owner: Product
depends_on:
  - Dashboard
  - Transactions
  - Budget Card
  - Progress Bars
  - Toasts
  - Modals
related:
  - Analytics
  - Settings
---

# Budgets

> **Budgets help users plan their spending before it happens—not explain it afterwards.**

---

# Purpose

The Budgets feature allows users to define spending limits and monitor progress throughout the month.

Budgets transform transaction data into proactive financial guidance by comparing planned spending against actual spending.

Every budget should answer one question:

**"Am I on track?"**

---

# User Goals

Users visit the Budgets feature to:

* Set a monthly budget.
* Create category-specific budgets.
* Monitor budget progress.
* Identify overspending early.
* Adjust budgets when circumstances change.

---

# Screen Layout

```text
┌────────────────────────────────────────────────────────────────────────────┐
│ Budgets                                                  July 2026 ▼       │
├────────────────────────────────────────────────────────────────────────────┤
│ Monthly Budget Card                                        Edit Budget      │
├────────────────────────────────────────────────────────────────────────────┤
│ Category Budgets                                                     + Add │
├────────────────────────────────────────────────────────────────────────────┤
│ Food        ███████░░░░░ 62%       ₹6,200 / ₹10,000                    │
│ Travel      ██████████░░ 84%       ₹4,200 / ₹5,000                     │
│ Groceries   ███░░░░░░░░░ 28%       ₹1,400 / ₹5,000                     │
├────────────────────────────────────────────────────────────────────────────┤
│ Budget Summary & Recommendations                                        │
└────────────────────────────────────────────────────────────────────────────┘
```

---

# Primary Components

| Component            | Required |
| -------------------- | -------- |
| Monthly Budget Card  | Yes      |
| Category Budget List | Yes      |
| Progress Bars        | Yes      |
| Budget Summary       | Yes      |
| Edit Budget Action   | Yes      |

---

# Budget Types

Version 1 supports:

## Monthly Budget

A single overall spending limit for the selected month.

Example:

```text
₹30,000
```

---

## Category Budget

Optional spending limits for individual categories.

Examples:

* Food
* Travel
* Groceries
* Entertainment
* Shopping

Categories without budgets continue tracking normally.

---

# Budget Creation

Users may create:

* One monthly budget.
* Zero or more category budgets.

Budgets are created through a simple form.

Required fields:

* Budget amount

Optional:

* Category
* Notes (future)

---

# Budget Editing

Users may edit:

* Monthly budget.
* Category budgets.

Changes should immediately update:

* Dashboard
* Budget Cards
* Insights
* Analytics

---

# Budget Progress

Every budget displays:

* Budget amount
* Amount spent
* Remaining amount
* Progress percentage
* Status

Progress uses the shared Progress Bar component.

---

# Budget Status

| Progress | Status            |
| -------- | ----------------- |
| 0–79%    | On Track          |
| 80–99%   | Approaching Limit |
| 100%+    | Over Budget       |

Status colors follow the Design System.

---

# Remaining Budget

Always display remaining budget.

Examples:

```text
Remaining ₹12,400
```

If exceeded:

```text
Over budget by ₹1,850
```

Never display negative remaining values.

---

# Budget Recommendations

Version 1 displays simple recommendations.

Examples:

* Food spending is approaching its limit.
* You are comfortably below your monthly budget.
* Travel spending exceeded your planned budget.

Recommendations should be factual and based solely on user data.

---

# Month Selection

Budgets are monthly.

Changing the selected month updates:

* Budget amounts
* Progress
* Recommendations
* Related dashboard metrics

Budgets should never combine data from different months.

---

# User Flows

## Create Monthly Budget

```text
Budgets

↓

Create Budget

↓

Save

↓

Dashboard Updates
```

---

## Update Budget

```text
Budgets

↓

Edit Budget

↓

Save

↓

Progress Recalculated
```

---

# Business Rules

* Budgets apply only to expense transactions.
* Income does not contribute to budget utilization.
* Category budgets contribute independently.
* Budget calculations update immediately after transaction changes.
* Budget percentages may exceed 100%.

---

# Empty State

Display:

```text
No budgets configured.

Create a monthly budget to
start tracking your spending goals.
```

Primary action:

**Create Budget**

---

# Loading State

Display:

* Skeleton Budget Card.
* Skeleton category list.
* Skeleton Progress Bars.

Maintain layout stability.

---

# Error State

Display:

```text
Unable to load budgets.

Please try again.
```

Offer a Retry action where appropriate.

---

# Keyboard Shortcuts

| Shortcut     | Action         |
| ------------ | -------------- |
| Ctrl/Cmd + N | Create Budget  |
| Esc          | Cancel editing |

---

# Performance Expectations

The Budgets screen should:

* Open in under two seconds.
* Recalculate immediately after transaction changes.
* Support dozens of category budgets without noticeable delay.

---

# Accessibility

The Budgets feature must:

* Support keyboard navigation.
* Announce progress changes to assistive technologies.
* Provide text alternatives for progress indicators.
* Maintain sufficient color contrast for status indicators.

---

# Acceptance Criteria

The Budgets feature is complete when:

* Users can create, edit, and remove budgets.
* Budget progress updates automatically.
* Dashboard reflects current budget status.
* Category budgets calculate correctly.
* Empty, loading, and error states are implemented.
* Accessibility requirements are satisfied.

---

# Future Enhancements

Future versions may introduce:

* Weekly budgets.
* Rolling budgets.
* Budget templates.
* Budget rollover.
* AI-generated budget recommendations.
* Shared household budgets.

These enhancements should extend the existing budgeting model while preserving its simplicity.

---

# Goal

The Budgets feature should help users make informed spending decisions before they exceed their limits.

A successful budget is not one that is never exceeded—it is one that helps users understand their spending and adjust it with confidence.
