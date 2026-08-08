---
title: Grid
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - ../README.md
  - Spacing.md
  - ../components/README.md
  - Responsive.md
  - ../../foundation/Product-Blueprint.md
---

# Grid System

> **A predictable layout creates a predictable experience.**

---

# Purpose

This document defines the layout grid used throughout FinTrack.

Every page, component, and screen must align to this grid system.

The grid provides:

* Visual consistency
* Predictable alignment
* Responsive behavior
* Scalable layouts
* Simplified implementation

No screen should define its own custom layout rules.

---

# Design Philosophy

Users should never consciously notice the grid.

They should simply feel that everything is aligned, balanced, and intentional.

Good grids disappear.

Bad grids become obvious.

---

# Grid Principles

Every layout should satisfy the following principles.

* Consistent alignment.
* Predictable spacing.
* Flexible responsiveness.
* Minimal nesting.
* Maximum readability.

---

# Container

All application content should live inside a responsive container.

| Property          |  Value |
| ----------------- | -----: |
| Max Width         | 1440px |
| Min Width         |  320px |
| Width             |   100% |
| Horizontal Margin |   Auto |

The container centers all desktop content.

---

# Page Padding

Page padding uses the spacing tokens defined in `Spacing.md`.

| Device  | Padding        |
| ------- | -------------- |
| Desktop | space-7 (48px) |
| Tablet  | space-6 (32px) |
| Mobile  | space-4 (16px) |

Content should never touch the viewport edge.

---

# Breakpoints

FinTrack supports four responsive breakpoints.

| Name    |       Width |
| ------- | ----------: |
| Mobile  |     0–639px |
| Tablet  |  640–1023px |
| Laptop  | 1024–1439px |
| Desktop |     1440px+ |

These breakpoints apply consistently across the application.

---

# Grid Columns

## Desktop

12 columns

---

## Laptop

12 columns

---

## Tablet

8 columns

---

## Mobile

4 columns

No alternative grid configurations should be introduced.

---

# Column Gutters

| Device  | Gutter |
| ------- | ------ |
| Desktop | 24px   |
| Laptop  | 24px   |
| Tablet  | 20px   |
| Mobile  | 16px   |

Column spacing should remain visually proportional across screen sizes.

---

# Vertical Rhythm

Sections stack vertically using the spacing system.

Recommended section spacing:

```text
space-7
```

Cards within a section:

```text
space-5
```

Related controls:

```text
space-2
```

---

# Dashboard Layout

The dashboard follows a two-level hierarchy.

## Hero Area

Full-width.

Contains:

* Summary cards
* Command Palette

---

## Content Area

Responsive grid.

Contains:

* Budget Overview
* Spending Breakdown
* Trends
* Recent Transactions
* Insights

Cards reflow automatically based on available columns.

---

# Card Placement

Cards should span whole columns.

Avoid fractional alignment.

Recommended widths:

| Columns | Usage            |
| ------: | ---------------- |
|       3 | Summary Card     |
|       4 | Budget Card      |
|       6 | Large Chart      |
|      12 | Full-width Table |

These values are recommendations, not rigid constraints.

---

# Nested Layouts

Avoid nesting grids more than one level deep.

Preferred:

```text
Page
 ├── Grid
      ├── Card
      ├── Card
      └── Card
```

Avoid:

```text
Grid
 └── Grid
      └── Grid
           └── Grid
```

Excessive nesting increases implementation complexity and reduces maintainability.

---

# Alignment Rules

All content aligns to the same column system.

Examples:

✔ Card titles align.

✔ Buttons align.

✔ Tables align.

✔ Charts align.

Misaligned components reduce visual trust.

---

# Maximum Line Length

Readable text should not exceed approximately:

**75 characters per line**

Long paragraphs should be constrained for readability.

---

# Full-Width Components

Only the following components may span the full container width:

* Navigation
* Dashboard Hero
* Transaction Table
* Settings Sections

Charts and cards should generally occupy grid columns rather than full width.

---

# Responsive Behavior

## Desktop → Tablet

Reduce column count.

Maintain content hierarchy.

Avoid horizontal scrolling.

---

## Tablet → Mobile

Cards stack vertically.

Summary cards become a carousel **only if** horizontal space becomes insufficient.

Otherwise, preserve vertical stacking.

---

# Dashboard Priority

On smaller screens, content should appear in this order:

1. Command Palette
2. Summary
3. Budget
4. Recent Transactions
5. Insights
6. Charts

The most actionable information should always appear first.

---

# Implementation Recommendation

Use CSS Grid for page layouts.

Example:

```css
display: grid;
grid-template-columns: repeat(12, 1fr);
gap: var(--space-5);
```

Individual components may use Flexbox internally where appropriate.

Use Grid for macro layout.

Use Flexbox for micro layout.

---

# Rules

Do:

* Align to the documented grid.
* Use spacing tokens.
* Respect breakpoints.
* Maintain consistent gutters.

Do not:

* Hardcode widths.
* Create custom grid systems.
* Mix unrelated spacing values.
* Use absolute positioning for layout.

---

# Definition of Done

A layout is complete when:

* All content aligns to the grid.
* Responsive behavior matches documented breakpoints.
* Components maintain consistent gutters.
* No horizontal scrolling occurs at supported viewport sizes.
* Layout remains visually balanced across all devices.

---

# Closing

A strong grid is invisible.

Users should never think about alignment.

They should simply experience an interface that feels ordered, predictable, and effortless to navigate.
