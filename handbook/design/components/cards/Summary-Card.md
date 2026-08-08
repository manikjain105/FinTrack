---
title: Summary Cards
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - Base-Card.md
  - ../../foundation/Typography.md
  - ../../foundation/Colors.md
  - ../../foundation/Spacing.md
  - ../../foundation/Motion.md
  - ../../../foundation/Product-Blueprint.md
---

# Summary Cards

> **Summary Cards answer the question: "What is happening right now?"**

---

# Purpose

Summary Cards present the most important financial metrics at a glance.

They are the first data components users see after opening FinTrack.

A Summary Card communicates one key metric and its immediate context.

It should never contain charts, tables, or complex interactions.

---

# Design Philosophy

Summary Cards are designed for rapid scanning.

Users should understand the financial state of the current month within a few seconds.

The numeric value is always the primary focus.

Supporting information exists only to provide context.

---

# Inheritance

Summary Cards inherit all specifications from `Cards.md`.

This document defines only the additional behavior and layout unique to Summary Cards.

---

# Version 1 Metrics

The dashboard contains exactly four Summary Cards.

1. Total Spent
2. Remaining Budget
3. Total Income
4. Net Savings

Additional summary metrics require a documented product decision.

---

# Layout

```text
┌──────────────────────────────┐
│ Total Spent                  │
│                              │
│ ₹18,420                      │
│                              │
│ ▲ ₹1,250 vs last month       │
└──────────────────────────────┘
```

Every Summary Card contains:

* Metric label
* Primary value
* Supporting comparison

No additional content should appear.

---

# Information Hierarchy

Visual priority:

1. Primary value
2. Metric title
3. Trend indicator
4. Supporting description

Users should notice the value before reading anything else.

---

# Primary Value

Typography:

Display

Weight:

700

Examples:

```text
₹18,420

₹82,350

₹2,14,980
```

All values use the configured currency format.

---

# Metric Title

Typography:

Body

Weight:

600

Examples:

* Total Spent
* Remaining Budget
* Income
* Savings

Titles should remain concise.

---

# Trend Indicator

Every Summary Card should communicate change whenever historical data exists.

Examples:

```text
▲ ₹2,450 compared to last month

▼ ₹980 compared to last month

No change from last month
```

Trend indicators should use semantic colors.

---

# Trend Icons

Use only:

* TrendingUp
* TrendingDown
* Minus

Icons reinforce the trend but never replace text.

---

# Color Rules

The primary value uses the standard text color.

Trend indicators use semantic colors.

| State    | Token          |
| -------- | -------------- |
| Positive | Success        |
| Neutral  | Text Secondary |
| Negative | Danger         |

Do not color the primary value based on performance.

Consistency is more important than emotional emphasis.

---

# Interaction

Summary Cards are informational by default.

They are not clickable.

Future versions may optionally allow navigation to detailed reports.

---

# Loading State

While loading:

* Preserve card dimensions.
* Display skeleton placeholders.
* Avoid layout shifts.

Users should immediately understand that data is being loaded.

---

# Empty State

If insufficient data exists:

```text
Total Spent

₹0

No transactions recorded yet.
```

Do not hide Summary Cards simply because the dataset is empty.

---

# Error State

If a metric cannot be calculated:

Display:

```text
Unable to calculate.

Please try again.
```

Errors should remain confined to the affected card.

---

# Responsive Behavior

Desktop:

Four cards displayed in a single row.

Tablet:

Two cards per row.

Mobile:

Single-column layout.

Cards should never become horizontally scrollable.

---

# Accessibility

Each Summary Card must expose:

* Metric name
* Current value
* Comparison text

Screen readers should announce the complete summary in a meaningful order.

Example:

> Total Spent. ₹18,420. Increased by ₹1,250 compared to last month.

---

# Anti-Patterns

Do not:

* Add multiple metrics to one Summary Card.
* Embed charts inside Summary Cards.
* Display unnecessary actions.
* Use decorative icons.
* Change card height based on content.

Every Summary Card should maintain visual consistency.

---

# Implementation Tokens

```css
--summary-card-min-height: 180px;
--summary-card-gap: var(--space-4);
--summary-value-font: var(--font-display);
```

---

# Definition of Done

A Summary Card implementation is complete when:

* It displays one metric only.
* The primary value is visually dominant.
* Trend information is clearly presented.
* Responsive behavior matches this specification.
* Accessibility requirements are satisfied.

---

# Implementation Notes

### Frontend

* Implement a reusable `<SummaryCard />` component extending the base `<Card />`.
* Accept props such as `title`, `value`, `trend`, `trendDirection`, and `comparisonText`.
* Keep layout fixed regardless of metric value length.

### Backend

* Provide precomputed summary metrics where practical.
* Return comparison values alongside the primary metric to avoid duplicate calculations.

### AI Coding Agent

* Never place charts or tables inside Summary Cards.
* Always inherit styling from the base Card component.
* Keep the component focused on presenting one key metric.

---

# Future Considerations

Future versions may introduce:

* Configurable summary metrics.
* Sparkline previews.
* Custom dashboard ordering.
* Multi-currency summaries.

These enhancements must preserve the simple, scan-friendly nature of Summary Cards.

---

# Closing

Summary Cards establish the first impression of the dashboard.

Users should understand the state of their finances in seconds, with one glance at four carefully designed metrics.

The less users need to interpret, the more valuable the Summary Cards become.
