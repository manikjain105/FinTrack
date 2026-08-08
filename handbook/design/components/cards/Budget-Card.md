---
title: Budget Cards
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - Base-Card.md
  - Summary-Card.md
  - ../Progress-Bars.md
  - ../../foundation/Colors.md
  - ../../foundation/Typography.md
  - ../../foundation/Spacing.md
  - ../../../foundation/Product-Blueprint.md
---

# Budget Cards

> **Budget Cards answer the question: "Am I on track?"**

---

# Purpose

Budget Cards visualize spending progress against a predefined budget.

Unlike Summary Cards, which report a single metric, Budget Cards combine related financial information into a single, actionable view.

Every Budget Card should help users determine whether they are spending within acceptable limits.

---

# Design Philosophy

Budget Cards should encourage awareness rather than anxiety.

The interface should communicate financial health calmly.

Users should immediately understand:

* Budget amount
* Amount spent
* Remaining amount
* Spending progress
* Current status

without reading large amounts of text.

---

# Inheritance

Budget Cards inherit all behavior from `Cards.md`.

This document defines only the behavior unique to Budget Cards.

---

# Information Hierarchy

Visual priority:

1. Progress
2. Amount spent
3. Remaining budget
4. Budget limit
5. Status
6. Supporting information

Progress is the primary visual indicator.

Numbers remain the primary source of truth.

---

# Standard Layout

```text
┌─────────────────────────────────────┐
│ Monthly Budget                      │
│                                     │
│ ₹18,420 of ₹30,000                  │
│ ███████████░░░░░░░░░░ 61%            │
│                                     │
│ Remaining ₹11,580                   │
│ On track for this month             │
└─────────────────────────────────────┘
```

---

# Required Elements

Every Budget Card contains:

* Title
* Current spend
* Budget amount
* Progress bar
* Remaining amount
* Budget status

Optional:

* Projected month-end spend
* Days remaining
* Category icon

---

# Progress Bar

Budget Cards must use the shared Progress Bar component.

Do not implement custom progress indicators.

Height:

```text
8px
```

Radius:

```text
radius-full
```

Animation:

```text
motion-normal
```

---

# Budget Status

Exactly one status should be displayed.

| Status            | Meaning                            |
| ----------------- | ---------------------------------- |
| On Track          | Spending comfortably within budget |
| Approaching Limit | Spending nearing budget            |
| Over Budget       | Budget exceeded                    |

Status messaging should remain concise.

---

# Status Thresholds

| Progress | Status            | Color   |
| -------- | ----------------- | ------- |
| 0–79%    | On Track          | Success |
| 80–99%   | Approaching Limit | Warning |
| 100%+    | Over Budget       | Danger  |

These thresholds apply consistently across the application.

---

# Remaining Budget

Remaining budget is always displayed.

Example:

```text
Remaining ₹11,580
```

If the budget is exceeded:

```text
Over budget by ₹2,340
```

Never display negative remaining values.

---

# Forecast

When enough data exists, display:

```text
Projected Month-End

₹28,700
```

Projection should be calculated using current spending pace.

If insufficient data exists, omit the forecast rather than displaying unreliable estimates.

---

# Trend Message

One supporting sentence should summarize the situation.

Examples:

```text
On pace to finish below budget.

Current pace exceeds your monthly budget.

Spending is consistent with last month.

Excellent control this month.
```

Messages should be factual rather than judgmental.

---

# Color Rules

Only semantic tokens may be used.

Progress:

* Success
* Warning
* Danger

Background:

Surface

Primary text:

Text Primary

Supporting text:

Text Secondary

---

# Interaction

Budget Cards are informational.

Optional interaction:

Selecting a Budget Card may open a detailed category breakdown.

The card should not expose multiple competing actions.

---

# Loading State

Loading placeholders should preserve layout.

Skeleton elements:

* Title
* Primary value
* Progress bar
* Supporting text

Avoid layout shifts.

---

# Empty State

When no budget exists:

```text
No monthly budget configured.

Set a budget to start tracking your progress.
```

Include a secondary action:

**Set Budget**

---

# Error State

Display:

```text
Unable to calculate budget progress.

Please try again.
```

Errors should remain isolated to the card.

---

# Responsive Behavior

Desktop:

Standard horizontal layout.

Tablet:

Maintain full content.

Mobile:

Stack supporting information vertically.

The progress bar should remain full width.

---

# Accessibility

Screen readers should announce:

* Budget name
* Amount spent
* Budget limit
* Remaining amount
* Progress percentage
* Current status

Example:

> Monthly Budget. ₹18,420 spent out of ₹30,000. 61 percent used. ₹11,580 remaining. On Track.

---

# Anti-Patterns

Do not:

* Hide the budget amount.
* Display multiple progress bars.
* Use decorative gradients.
* Flash warning colors.
* Animate the progress bar continuously.

The component should feel calm and informative.

---

# Implementation Tokens

```css
--budget-card-min-height: 240px;
--budget-progress-height: 8px;
--budget-status-gap: var(--space-3);
```

---

# Definition of Done

A Budget Card implementation is complete when:

* Budget progress is accurately displayed.
* Semantic status colors are used.
* Remaining budget is always shown.
* Progress uses the shared Progress Bar component.
* Responsive behavior matches this specification.
* Accessibility requirements are satisfied.

---

# Implementation Notes

### Frontend

* Build `<BudgetCard />` by composing the base `<Card />` and `<ProgressBar />` components.
* Accept props such as `budget`, `spent`, `remaining`, `percentage`, `status`, and `projection`.
* Keep the layout stable regardless of value length.

### Backend

* Return precomputed budget metrics and projection values.
* Ensure percentage values are clamped between 0 and values exceeding 100% where appropriate.

### AI Coding Agent

* Never create a custom progress indicator.
* Always use semantic status thresholds.
* Preserve consistent spacing and hierarchy from the base Card component.

---

# Future Considerations

Future versions may introduce:

* Weekly budget tracking.
* Category-specific budget cards.
* Adaptive budget recommendations.
* Historical comparison sparklines.
* Customizable budget thresholds.

These enhancements must extend the existing Budget Card rather than replace it.

---

# Closing

A Budget Card should answer one question with complete confidence:

**"Am I on track this month?"**

If users can answer that question in a single glance, the component has achieved its purpose.
