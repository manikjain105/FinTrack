---
title: Insight Cards
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - Base-Card.md
  - Summary-Card.md
  - Budget-Card.md
  - ../../foundation/Typography.md
  - ../../foundation/Colors.md
  - ../../../foundation/Product-Blueprint.md
---

# Insight Cards

> **Insight Cards answer the question: "What should I know?"**

---

# Purpose

Insight Cards transform financial data into actionable observations.

Unlike Summary Cards, which present facts, or Budget Cards, which present progress, Insight Cards explain patterns, trends, and opportunities.

Every Insight Card should provide information that helps the user make a better financial decision.

---

# Design Philosophy

Insight Cards should never overwhelm users with statistics.

Each card should communicate one meaningful observation.

Insights should be:

* Relevant
* Timely
* Actionable
* Evidence-based

Avoid generic financial advice.

Insights should always be derived from the user's own data.

---

# Inheritance

Insight Cards inherit all structural behavior from `Base-Card.md`.

This document defines only the behavior unique to Insight Cards.

---

# Information Hierarchy

Visual priority:

1. Insight headline
2. Supporting explanation
3. Key figures
4. Suggested action

Users should understand the message before reading the numbers.

---

# Standard Layout

```text
┌──────────────────────────────────────────────┐
│ 💡 Food spending increased                   │
│                                              │
│ You spent ₹4,250 more on Food this month     │
│ than last month (+28%).                      │
│                                              │
│ Saving 20% would reduce annual spending by   │
│ approximately ₹10,200.                       │
└──────────────────────────────────────────────┘
```

---

# Required Elements

Every Insight Card contains:

* Insight title
* Explanation
* Supporting values
* Suggested takeaway

Optional:

* Trend icon
* Related category
* Confidence indicator (future versions)

---

# Insight Categories

Version 1 supports the following insight types:

| Type      | Example                                   |
| --------- | ----------------------------------------- |
| Trend     | Food spending increased by 18%            |
| Savings   | Reducing dining by 20% saves ₹12,000/year |
| Budget    | Entertainment budget exceeded             |
| Forecast  | Projected to exceed budget by ₹4,500      |
| Habit     | Ordered food 17 times this month          |
| Milestone | Highest monthly savings in six months     |
| Income    | Income increased compared to last month   |

Each card should belong to exactly one category.

---

# Writing Style

Insight headlines should be short.

Good examples:

* Food spending increased.
* You're on track this month.
* Savings improved.
* Rent remains stable.
* Grocery spending is decreasing.

Avoid vague headlines:

* Monthly Analysis
* Financial Report
* Expense Summary

The title should communicate the conclusion.

---

# Supporting Explanation

The explanation should:

* Include actual numbers.
* Mention the relevant period.
* Be easy to understand.

Example:

```text
Food spending increased by ₹4,250
compared to last month (+28%).
```

Avoid percentages without actual amounts.

---

# Suggested Action

Where appropriate, suggest one action.

Examples:

```text
Reducing restaurant spending by 20%
could save approximately ₹14,000 per year.
```

```text
You're comfortably below budget.
Consider increasing your monthly SIP.
```

Suggestions should remain optional.

Never sound prescriptive.

---

# Insight Priority

If multiple insights exist, display them in this order:

1. Overspending alerts
2. Budget forecasts
3. Savings opportunities
4. Spending trends
5. Spending habits
6. Milestones

Only the most valuable insights should appear on the dashboard.

---

# Maximum Insights

Dashboard:

Maximum:

```text
3 Insight Cards
```

Users should not need to scroll through dozens of recommendations.

---

# Color Rules

Most Insight Cards use neutral styling.

Use semantic colors only when they communicate state.

Examples:

* Success → Savings opportunity
* Warning → Approaching budget
* Danger → Budget exceeded

Avoid coloring entire cards.

Use subtle visual emphasis.

---

# Icons

Recommended icons:

| Insight    | Icon          |
| ---------- | ------------- |
| Savings    | PiggyBank     |
| Trend Up   | TrendingUp    |
| Trend Down | TrendingDown  |
| Budget     | Wallet        |
| Alert      | TriangleAlert |
| Habit      | Calendar      |
| Milestone  | Trophy        |

Icons support recognition but never replace the headline.

---

# Interaction

Insight Cards are optional entry points.

If clicked, they may navigate to:

* Category details
* Monthly analytics
* Transaction list

Avoid multiple actions within a single card.

---

# Empty State

If insufficient history exists:

```text
Keep using FinTrack.

Insights will appear once enough data has been collected.
```

Do not generate artificial insights.

---

# Loading State

Display skeleton placeholders.

Preserve card height to avoid layout shifts.

---

# Error State

Display:

```text
Unable to generate insights.

Please try again later.
```

Errors should remain isolated to the affected card.

---

# Accessibility

Screen readers should announce:

* Insight title
* Supporting explanation
* Suggested action

Icons should not be relied upon to communicate meaning.

---

# Anti-Patterns

Do not:

* Invent insights without supporting data.
* Repeat the same insight in different wording.
* Display generic financial advice.
* Shame users for spending.
* Use emotional or judgmental language.

Insights should inform—not criticize.

---

# Implementation Tokens

```css
--insight-card-min-height: 220px;
--insight-gap: var(--space-4);
--insight-icon-size: var(--icon-lg);
```

---

# Definition of Done

An Insight Card implementation is complete when:

* The insight is derived from real user data.
* Supporting figures are included.
* Suggested actions are evidence-based.
* The card follows the shared Card specification.
* Accessibility requirements are satisfied.

---

# Implementation Notes

### Frontend

* Implement a reusable `<InsightCard />` component extending the base `<Card />`.
* Accept props such as `title`, `description`, `type`, `values`, `action`, and `icon`.
* Preserve a consistent height across all displayed insights.

### Backend

* Generate insights from aggregated transaction data.
* Prioritize insights based on usefulness rather than quantity.
* Return structured insight objects rather than preformatted text.

### AI Coding Agent

* Never fabricate insights.
* Display only high-confidence observations.
* Limit dashboard insights to the three highest-priority items.
* Keep the language factual, concise, and encouraging.

---

# Future Considerations

Future versions may introduce:

* AI-generated spending explanations.
* Personalized savings goals.
* Investment recommendations.
* Seasonal spending analysis.
* Predictive financial coaching.

These enhancements must remain grounded in user data and maintain the calm, trustworthy tone of FinTrack.

---

# Closing

Insight Cards are where FinTrack becomes more than an expense tracker.

They transform historical data into useful guidance.

A successful Insight Card doesn't just tell users what happened.

It helps them understand what to do next.
