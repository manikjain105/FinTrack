---
title: Empty States
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - cards/Base-Card.md
  - Buttons.md
  - Command-Palette.md
  - ../foundation/Icons.md
  - ../foundation/Typography.md
  - ../foundation/Spacing.md
  - ../foundation/Colors.md
---

# Empty States

> **An empty state should teach users what to do next.**

---

# Purpose

Empty States communicate that no content is currently available while guiding users toward the next meaningful action.

An empty state should never feel like an error.

Instead, it should reassure users that the application is ready and explain how to get started.

---

# Design Philosophy

Every empty state should answer three questions:

1. Why is this empty?
2. Is that expected?
3. What should I do next?

Users should never feel stuck.

---

# Design Principles

Every empty state should:

* Explain the situation.
* Encourage the next action.
* Remain visually calm.
* Match the surrounding layout.
* Avoid blaming the user.

---

# Standard Layout

```text
📄

No transactions yet

Start tracking your expenses by typing:

coffee 180

[Add First Transaction]
```

---

# Anatomy

Every empty state contains:

* Illustration or icon
* Title
* Short explanation
* Primary action

Optional:

* Secondary action
* Example
* Documentation link (future)

---

# Titles

Titles should be short.

Good examples:

* No transactions yet
* No budgets configured
* No analytics available
* No insights yet

Avoid vague titles:

* Empty
* Nothing Here
* No Data

The title should explain what is missing.

---

# Supporting Text

The description should explain why the content is empty.

Example:

```text
Start recording transactions to
unlock spending trends and insights.
```

Descriptions should remain concise.

---

# Primary Action

Every empty state should offer exactly one primary action.

Examples:

| Empty State  | Action                   |
| ------------ | ------------------------ |
| Transactions | Add Transaction          |
| Budget       | Set Budget               |
| Analytics    | Record First Transaction |
| Search       | Clear Filters            |

The action should move the user toward filling the empty state.

---

# Examples

When appropriate, include a realistic example.

Examples:

```text
coffee 180

uber 260

salary 75000
```

Examples reduce hesitation and teach users the Command Palette naturally.

---

# Illustrations

Version 1 uses simple outline icons.

Avoid:

* Large illustrations.
* Decorative artwork.
* Mascots.
* Animations.

The illustration supports the message without becoming the focal point.

---

# Empty State Types

## First-Time Use

Shown when no user data exists.

Should feel welcoming.

---

## Filtered Results

Shown when filters remove all results.

Example:

```text
No transactions match your filters.
```

Offer:

**Clear Filters**

---

## Search Results

Example:

```text
No matching transactions found.
```

Encourage the user to try another search term.

---

## Feature Not Yet Used

Example:

```text
Create your first monthly budget
to start tracking your progress.
```

These states introduce features gradually.

---

# Dashboard

The dashboard should never appear empty.

Even without transactions, display:

* Summary cards with zero values.
* Command Palette.
* Helpful empty-state cards.

The interface should feel complete from day one.

---

# Charts

Empty charts should not display blank axes.

Instead, display:

```text
Record more transactions to
see spending trends.
```

---

# Insights

Example:

```text
Insights will appear after
you've recorded a few days
of spending.
```

Never generate placeholder insights.

---

# Budgets

Example:

```text
You haven't created a budget yet.

Set one to monitor
your monthly spending.
```

---

# Loading vs Empty

Never confuse the two.

Loading:

> Data is coming.

Empty:

> There is currently no data.

These states communicate fundamentally different situations.

---

# Accessibility

Every empty state must include:

* Readable heading.
* Descriptive text.
* Keyboard-accessible action.
* Screen reader-friendly structure.

Icons should use:

```html
aria-hidden="true"
```

---

# Responsive Behavior

Empty states should remain centered.

Content width:

Maximum:

```text
480px
```

Maintain generous whitespace on all devices.

---

# Anti-Patterns

Do not:

* Display blank pages.
* Show technical messages.
* Use humor during errors.
* Blame the user.
* Leave users without an obvious next step.

Every empty state should encourage progress.

---

# Implementation Tokens

```css
--empty-state-max-width: 480px;
--empty-state-gap: var(--space-4);

--empty-state-icon-size: var(--icon-xl);
```

---

# Definition of Done

An empty state is complete when:

* It explains why the page is empty.
* It offers a meaningful next action.
* It matches the surrounding layout.
* Accessibility requirements are satisfied.
* The page never feels unfinished.

---

# Implementation Notes

### Frontend

* Create a reusable `<EmptyState />` component.
* Accept props such as `title`, `description`, `action`, `icon`, and `example`.
* Reuse the component across all features rather than creating page-specific versions.

### Backend

* Return explicit empty datasets rather than treating them as errors.
* Differentiate between "no results" and "failed request."

### AI Coding Agent

* Never render blank pages when data is absent.
* Always provide one clear next action.
* Tailor the empty-state message to the current feature while reusing the shared component.

---

# Future Considerations

Future versions may introduce:

* Personalized onboarding tips.
* Context-aware recommendations.
* Interactive walkthroughs.
* Sample demo data.

These enhancements should complement—not replace—the simple, action-oriented empty state defined here.

---

# Closing

An empty state is the application's first conversation with a new user.

Instead of saying,

*"There's nothing here,"*

it should say,

*"Here's how to get started."*

When users instinctively know their next step, the empty state has done its job.
