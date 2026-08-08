---
title: Cards
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - ../../README.md
  - ../../foundation/Colors.md
  - ../../foundation/Typography.md
  - ../../foundation/Spacing.md
  - ../../foundation/Borders-and-Radius.md
  - ../../foundation/Elevation.md
  - ../../foundation/Grid.md
  - ../../foundation/Motion.md
---

# Cards

> **Cards organize information. They should never compete for attention.**

---

# Purpose

Cards are the primary layout container in FinTrack.

A card groups related information into a single visual unit.

Every card should answer **one question**.

If a card answers multiple unrelated questions, it should be split into separate cards.

---

# Design Philosophy

Cards provide structure.

They are not decorative.

Users should notice the information inside the card—not the card itself.

The interface should feel calm, spacious, and predictable.

---

# Card Principles

Every card should:

* Have one clear purpose.
* Be visually lightweight.
* Follow the design token system.
* Adapt gracefully to different screen sizes.
* Maintain consistent internal spacing.

---

# Standard Specifications

| Property      |          Value |
| ------------- | -------------: |
| Border Radius |      radius-xl |
| Border        |       border-1 |
| Border Color  | border-default |
| Elevation     |    elevation-1 |
| Padding       |        space-5 |
| Background    |        Surface |
| Transition    |  motion-normal |

These values apply to every standard card unless explicitly overridden.

---

# Card Anatomy

Every card follows the same structure.

```text
┌─────────────────────────────────────┐
│ Header                              │
│ Optional Description                │
├─────────────────────────────────────┤
│                                     │
│ Main Content                        │
│                                     │
├─────────────────────────────────────┤
│ Optional Footer / Actions           │
└─────────────────────────────────────┘
```

Sections that are not needed should simply be omitted.

Never insert empty placeholders.

---

# Header

The header should contain:

* Title (required)
* Optional subtitle
* Optional actions

Header actions should remain minimal.

Examples:

* Export
* Refresh
* View All

---

# Content

The content area contains the primary information.

Examples:

* Financial metrics
* Charts
* Lists
* Tables
* Insights
* Forms

Content determines the height of the card.

Avoid fixed heights unless necessary.

---

# Footer

Footers are optional.

Use them only for:

* Secondary actions
* Supporting metadata
* Status summaries

Avoid placing primary actions in the footer.

---

# Card Width

Cards should occupy whole grid columns.

Recommended spans:

| Columns | Usage            |
| ------: | ---------------- |
|       3 | Summary Card     |
|       4 | Budget Card      |
|       6 | Analytics Card   |
|      12 | Full-width Table |

---

# Hover Behavior

Static cards:

No hover effect.

Interactive cards:

* Elevation increases to elevation-2.
* Border color subtly changes.
* Cursor becomes pointer.

Hover should indicate interactivity, not decoration.

---

# Clickable Cards

Clickable cards should be used sparingly.

Suitable examples:

* Navigate to transaction details.
* Open category breakdown.
* View monthly report.

Do not make informational cards clickable without a clear destination.

---

# Responsive Behavior

Desktop:

Cards align to the grid.

Tablet:

Cards reflow naturally.

Mobile:

Cards stack vertically.

Maintain consistent spacing between cards across all breakpoints.

---

# Empty Cards

Cards with no data should remain useful.

Example:

```text
No expenses recorded yet.

Start by typing:

coffee 180
```

An empty card should always encourage the next action.

---

# Loading State

Cards should preserve their layout while loading.

Use skeleton placeholders.

Avoid collapsing card height during loading.

---

# Error State

If a card cannot display its content:

* Explain the problem.
* Offer a retry action when appropriate.
* Preserve the surrounding layout.

Errors should remain isolated to the affected card.

---

# Accessibility

Cards must support:

* Keyboard navigation (if interactive).
* Visible focus state.
* Proper semantic structure.
* Screen reader compatibility.

Interactive cards should use appropriate ARIA roles.

---

# Anti-Patterns

Do not:

* Nest multiple cards inside another card.
* Mix unrelated content.
* Add unnecessary shadows.
* Use different padding values.
* Create unique card styles for individual screens.

Consistency is more valuable than novelty.

---

# Implementation Tokens

```css
--card-radius: var(--radius-xl);
--card-padding: var(--space-5);
--card-border: var(--border-1);
--card-shadow: var(--shadow-sm);
--card-background: var(--color-surface);
```

---

# Definition of Done

A card implementation is complete when:

* It follows documented design tokens.
* Internal spacing is consistent.
* It supports responsive layouts.
* Interactive states are implemented where applicable.
* Accessibility requirements are satisfied.

---

# Implementation Notes

### Frontend

* Create a reusable `<Card />` component with optional `Header`, `Content`, and `Footer` slots.
* Build all specialized cards by composing the base Card component.
* Avoid duplicating card styles across feature modules.

### Backend

* Not applicable.

### AI Coding Agent

* Never build custom containers when a Card component satisfies the requirement.
* Extend the base Card instead of copying styles.
* Keep cards focused on a single responsibility.

---

# Future Considerations

Future versions may introduce:

* Collapsible cards.
* Resizable dashboard cards.
* User-customizable dashboard layouts.
* Drag-and-drop card reordering.

These capabilities should extend the base Card component rather than replace it.

---

# Closing

Cards are the structural language of FinTrack.

A well-designed card quietly organizes information, reduces cognitive load, and allows users to focus on their finances instead of the interface.
