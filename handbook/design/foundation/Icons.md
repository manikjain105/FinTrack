---
title: Icons
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - ../README.md
  - Colors.md
  - Typography.md
  - ../components/Buttons.md
  - ../../foundation/Product-Blueprint.md
---

# Icons

> **Icons support understanding. They never replace words.**

---

# Purpose

This document defines the icon system used throughout FinTrack.

Icons exist to improve recognition, reduce visual scanning, and reinforce meaning.

They should never introduce ambiguity.

Users should always understand an interface even if every icon is removed.

---

# Icon Philosophy

Icons are supporting elements.

Text communicates.

Icons reinforce.

If an icon is required for users to understand an action, the interface should be redesigned.

---

# Icon Library

Version 1 uses:

## Lucide Icons

Reasons:

* Open source
* Consistent stroke style
* Tree-shakeable
* React-friendly
* Excellent coverage
* Modern appearance

No additional icon libraries should be introduced without approval.

---

# Style

Icons must follow a single visual style.

* Outline icons only.
* Rounded joins.
* Rounded caps.
* No filled icons.
* No skeuomorphic icons.
* No emoji.

Mixing styles is prohibited.

---

# Standard Sizes

| Token   | Size | Usage           |
| ------- | ---- | --------------- |
| icon-xs | 12px | Metadata        |
| icon-sm | 16px | Inline labels   |
| icon-md | 20px | Buttons, inputs |
| icon-lg | 24px | Navigation      |
| icon-xl | 32px | Empty states    |

Only these sizes are permitted.

---

# Stroke Width

Standard stroke:

```text
2px
```

Do not override stroke width for individual icons.

---

# Semantic Usage

Use consistent icons for the same concepts.

| Concept      | Recommended Icon |
| ------------ | ---------------- |
| Dashboard    | LayoutDashboard  |
| Transactions | Receipt          |
| Search       | Search           |
| Budget       | Wallet           |
| Income       | ArrowDownCircle  |
| Expense      | ArrowUpCircle    |
| Settings     | Settings         |
| Export       | Download         |
| Import       | Upload           |
| Delete       | Trash2           |
| Edit         | Pencil           |
| Save         | Check            |
| Warning      | TriangleAlert    |
| Error        | CircleAlert      |
| Success      | CircleCheck      |

These mappings should remain stable across the application.

---

# Navigation

Navigation items should include:

* Icon
* Label

Icons must never appear without labels in primary navigation.

---

# Buttons

## Primary Buttons

Label is required.

Icon is optional.

Example:

```text
+ Add Transaction
```

---

## Icon Buttons

Reserved for:

* Edit
* Delete
* Search
* Filter
* Close

Every icon button must include an accessible label.

---

# Cards

Icons may be used in card headers to reinforce context.

Example:

* Wallet → Budget
* TrendingUp → Income
* ShoppingCart → Expenses

Avoid decorative icons inside data-heavy cards.

---

# Charts

Icons should not appear inside charts.

Icons may appear:

* In chart headers.
* In legends (if meaningful).

Never overlay icons on chart data.

---

# Empty States

Empty states may include one illustration-style icon.

Recommended size:

```text
32px
```

The icon should support the message without becoming the focal point.

---

# Color Usage

Icons inherit semantic color tokens.

Examples:

* Success → Success token
* Warning → Warning token
* Error → Danger token
* Default → Text Secondary

Do not introduce custom icon colors.

---

# Accessibility

Every interactive icon must include:

* Accessible name (`aria-label`)
* Keyboard focus
* Visible focus state

Decorative icons should use:

```html
aria-hidden="true"
```

Screen readers should ignore decorative icons.

---

# Spacing

Spacing between icon and text:

```text
space-2
```

Icons should align vertically with text baselines whenever possible.

---

# Anti-Patterns

Do not:

* Mix icon libraries.
* Use filled and outline icons together.
* Replace text with icons.
* Rotate icons without meaning.
* Use icons as decoration.

---

# Implementation

Install:

```bash
npm install lucide-react
```

Example:

```tsx
import { Search } from "lucide-react";

<Search size={20} />
```

Wrap common icons in a shared `Icon` component if additional behavior or theming is needed.

---

# Definition of Done

The icon system is complete when:

* Only Lucide icons are used.
* Sizes match documented tokens.
* Icons use semantic colors.
* Interactive icons are accessible.
* Primary navigation always includes labels.

---

# Implementation Notes

### Frontend

* Import icons directly from `lucide-react`.
* Avoid dynamic imports unless bundle size requires optimization.
* Expose standard icon sizes as reusable constants.

### Backend

* Not applicable.

### AI Coding Agent

* Never introduce a second icon library.
* Never replace labels with icons.
* Use documented semantic mappings wherever possible.

---

# Future Considerations

Future versions may introduce:

* Custom brand illustrations.
* Animated onboarding illustrations.
* Achievement icons.

These should complement—not replace—the core icon system.

---

# Closing

Icons should make interfaces easier to scan, not harder to understand.

When users stop noticing the icons and simply understand the interface, the icon system has succeeded.
