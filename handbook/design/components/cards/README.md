# Cards

Cards are the primary information containers in FinTrack.

Every dashboard section, insight, budget summary, and analytical view is built upon the shared Card component.

Rather than creating multiple unrelated card designs, FinTrack follows a strict inheritance model.

---

# Reading Order

Read the card specifications in the following order:

1. Base Card
2. Summary Card
3. Budget Card
4. Insight Card

Every specialized card inherits from the Base Card specification.

---

# Card Hierarchy

```text
Base Card
    │
    ├── Summary Card
    │
    ├── Budget Card
    │
    └── Insight Card
```

Future card types should extend the Base Card whenever possible.

---

# Philosophy

Cards exist to organize information.

They should never compete for attention.

Users should notice the information inside a card—not the card itself.

---

# Responsibilities

## Base Card

Defines:

* Layout
* Padding
* Borders
* Elevation
* Header
* Content
* Footer
* Responsive behavior

Every specialized card inherits these characteristics.

---

## Summary Card

Purpose:

Present one key metric.

Examples:

* Total Spent
* Remaining Budget
* Income
* Savings

Summary Cards prioritize speed of understanding.

---

## Budget Card

Purpose:

Visualize progress toward a financial budget.

Includes:

* Budget amount
* Current spending
* Remaining amount
* Progress bar
* Budget status
* Projection

---

## Insight Card

Purpose:

Transform financial data into actionable observations.

Examples:

* Spending trends
* Savings opportunities
* Budget forecasts
* Spending habits

Insight Cards explain what the data means rather than simply displaying it.

---

# Design Principles

Every card should:

* Solve one problem.
* Display one primary idea.
* Maintain consistent spacing.
* Reuse shared design tokens.
* Support responsive layouts.
* Preserve accessibility.

---

# What Does Not Belong Here

Do not create separate card styles for individual screens.

For example:

❌ Dashboard Card

❌ Analytics Card

❌ Settings Card

Instead:

Use the existing card types or extend the Base Card through a documented specialization.

---

# Future Expansion

Future versions of FinTrack may introduce additional card types such as:

* Chart Card
* Investment Card
* Goal Card
* Portfolio Card
* Alert Card

These should extend the Base Card rather than introducing entirely new design patterns.

---

# Goal

The Cards section ensures that every information container in FinTrack feels like part of the same product.

As the application grows, new cards should inherit existing behavior instead of redefining layout, spacing, or interaction from scratch.

Consistency is achieved through composition, not duplication.
