---
title: Dashboard
category: Product
status: Approved
version: 1.0
owner: Product
depends_on:
  - Design System
  - Application Shell
  - Base Card
  - Summary Card
  - Budget Card
  - Insight Card
  - Progress Bars
related:
  - Transactions
  - Budgets
  - Analytics
---

# Dashboard

> **The Dashboard is the financial home screen of FinTrack.**

---

# Purpose

The Dashboard provides an immediate overview of the user's financial health.

It should answer the most important financial questions without requiring navigation to other pages.

A user opening FinTrack should understand the current month's financial situation within a few seconds.

---

# User Goals

When visiting the Dashboard, users typically want to know:

* How much have I spent this month?
* Am I within my budget?
* Where is my money going?
* Has anything unusual happened?
* What should I pay attention to today?

The Dashboard should answer these questions immediately.

---

# Primary Users

The Dashboard is designed for:

* Daily expense tracking
* Weekly financial reviews
* Monthly budget monitoring

It is not intended for deep financial analysis.

Detailed exploration belongs in the Analytics section.

---

# Screen Layout

```text
┌────────────────────────────────────────────────────────────────────────────┐
│ Header                                                             July ▼ │
├────────────────────────────────────────────────────────────────────────────┤
│ Command Palette                                                    Ctrl+K │
├────────────────────────────────────────────────────────────────────────────┤
│ Summary Cards (4)                                                     │
├────────────────────────────────────────────────────────────────────────────┤
│ Budget Card                     │ Spending Trend Chart                   │
├─────────────────────────────────┼─────────────────────────────────────────┤
│ Category Breakdown              │ Insight Cards                          │
├─────────────────────────────────┼─────────────────────────────────────────┤
│ Recent Transactions                                               View All │
└────────────────────────────────────────────────────────────────────────────┘
```

---

# Information Hierarchy

The Dashboard should present information in this order:

1. Input (Command Palette)
2. Current financial status
3. Budget health
4. Spending trends
5. Category breakdown
6. Insights
7. Recent activity

Users should never need to scroll to add a transaction.

---

# Components

The Dashboard consists of:

| Component            | Required |
| -------------------- | -------- |
| Command Palette      | Yes      |
| Summary Cards        | Yes      |
| Budget Card          | Yes      |
| Spending Trend Chart | Yes      |
| Category Breakdown   | Yes      |
| Insight Cards        | Yes      |
| Recent Transactions  | Yes      |

No additional widgets should appear in Version 1.

---

# Summary Cards

Display exactly four metrics:

* Total Spent
* Remaining Budget
* Total Income
* Net Savings

These values update immediately after every transaction.

---

# Command Palette

The Command Palette is the fastest way to add transactions.

Examples:

```text
coffee 180

uber 240

salary 75000

rent 12000
```

Successful submission should:

1. Save the transaction.
2. Update all dashboard metrics.
3. Display a success toast.
4. Keep keyboard focus ready for the next entry.

---

# Budget Card

Display:

* Monthly budget
* Current spend
* Remaining budget
* Progress percentage
* Status
* Projected month-end spending

The Budget Card is always visible.

---

# Spending Trend

Show cumulative daily spending for the selected month.

Include:

* Actual spending
* Ideal budget pace

The chart should help users identify whether they are ahead of or behind their planned spending.

---

# Category Breakdown

Display spending by category.

Version 1 uses a donut chart.

Show:

* Amount
* Percentage
* Category name

Categories with zero spending should be omitted.

---

# Insight Cards

Display a maximum of three insights.

Priority:

1. Budget alerts
2. Savings opportunities
3. Spending trends

Insights should always be derived from actual data.

---

# Recent Transactions

Display the latest ten transactions.

Columns:

* Date
* Merchant
* Category
* Amount

Provide:

**View All**

to navigate to the Transactions screen.

---

# Month Selector

Users may switch between months.

Changing the month updates:

* Summary Cards
* Charts
* Budget
* Insights
* Transactions

The Dashboard should never mix data from different months.

---

# User Flows

## Adding a Transaction

```text
Dashboard

↓

Command Palette

↓

Transaction Saved

↓

Dashboard Updates

↓

Toast Confirmation
```

---

## Reviewing Monthly Progress

```text
Dashboard

↓

Summary Cards

↓

Budget Card

↓

Insights

↓

Analytics (optional)
```

---

# Business Rules

* Only transactions belonging to the selected month contribute to dashboard metrics.
* Income and expenses are calculated independently.
* Projections use the current daily spending pace.
* Insights should be recalculated whenever transaction data changes.

---

# Loading State

Display:

* Skeleton Summary Cards
* Skeleton Budget Card
* Chart placeholders
* Skeleton Recent Transactions

Maintain the final page layout while loading.

---

# Empty State

If no transactions exist:

Display:

* Zero-value Summary Cards
* Empty Budget Card
* Helpful onboarding message
* Example Command Palette entries

The Dashboard should still feel complete.

---

# Error State

If dashboard data cannot be loaded:

* Explain the issue.
* Preserve the page structure.
* Provide a Retry action.

Avoid displaying a blank screen.

---

# Keyboard Shortcuts

| Shortcut     | Action                |
| ------------ | --------------------- |
| Ctrl/Cmd + K | Focus Command Palette |
| ↑ / ↓        | Navigate suggestions  |
| Enter        | Submit transaction    |
| Esc          | Clear input           |

These shortcuts should work consistently across the application.

---

# Performance Expectations

The Dashboard should:

* Render within two seconds on typical hardware.
* Update metrics immediately after a transaction is saved.
* Avoid unnecessary re-rendering.
* Remain responsive with thousands of transactions.

---

# Accessibility

The Dashboard must:

* Be fully keyboard navigable.
* Announce updates to assistive technologies.
* Preserve logical heading hierarchy.
* Maintain sufficient color contrast.

Every chart should provide an accessible textual summary.

---

# Acceptance Criteria

The Dashboard is complete when:

* Users can add a transaction without leaving the page.
* All summary metrics update correctly.
* Budget progress reflects current spending.
* Charts display accurate monthly data.
* Recent Transactions show the latest entries.
* Empty, loading, and error states are implemented.
* Accessibility requirements are satisfied.

---

# Future Enhancements

Potential future additions include:

* Multiple dashboards.
* Goal tracking widgets.
* Investment summaries.
* Custom dashboard layouts.
* AI-generated weekly financial briefings.

These enhancements should extend the Dashboard without compromising its primary purpose as a fast financial overview.

---

# Goal

The Dashboard should become the screen users instinctively open whenever they want to understand their financial situation.

If users can answer **"How am I doing this month?"** in under ten seconds, the Dashboard has achieved its purpose.
