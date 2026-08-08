---
title: Spacing
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - ../README.md
  - Design-Principles.md
  - Typography.md
---

# Spacing

> **Consistent spacing creates calm interfaces.**

---

# Purpose

This document defines the spacing system used throughout FinTrack.

Every margin, padding, gap, and layout distance must use the spacing tokens defined here.

Arbitrary spacing values are not permitted.

A consistent spacing system creates rhythm, improves readability, and makes the interface feel intentional.

---

# Design Philosophy

Whitespace is not empty space.

Whitespace separates information.

Whitespace creates hierarchy.

Whitespace reduces cognitive load.

When in doubt, add clarity—not clutter.

---

# Spacing Scale

FinTrack uses an **8-point spacing system** with a few supporting values for fine adjustments.

| Token   | Value | Usage                |
| ------- | ----: | -------------------- |
| space-0 |   0px | No spacing           |
| space-1 |   4px | Micro spacing        |
| space-2 |   8px | Tight spacing        |
| space-3 |  12px | Small spacing        |
| space-4 |  16px | Default spacing      |
| space-5 |  24px | Card spacing         |
| space-6 |  32px | Large spacing        |
| space-7 |  48px | Section spacing      |
| space-8 |  64px | Major layout spacing |
| space-9 |  96px | Page spacing         |

No values outside this scale should be introduced without updating this document.

---

# Component Padding

## Buttons

Horizontal:

```text
space-4
```

Vertical:

```text
space-2
```

---

## Cards

Internal padding:

```text
space-5
```

Cards should always feel spacious.

Avoid cramped layouts.

---

## Input Fields

Horizontal padding:

```text
space-4
```

Vertical padding:

```text
space-3
```

The command palette follows the same padding rules.

---

## Tables

Cell padding:

```text
space-3
```

Header padding:

```text
space-4
```

---

# Layout Gaps

## Between cards

```text
space-5
```

---

## Between sections

```text
space-7
```

---

## Between related controls

```text
space-2
```

---

## Between unrelated groups

```text
space-6
```

---

# Page Layout

Desktop page padding:

```text
space-7
```

---

Tablet:

```text
space-6
```

---

Mobile:

```text
space-4
```

Content should never touch the screen edges.

---

# Grid Rhythm

Spacing should create a predictable rhythm.

Typical pattern:

```text
Heading

space-4

Description

space-5

Content

space-7

Next Section
```

Users should subconsciously recognize this rhythm across every screen.

---

# Card Layout

Cards should contain:

* Title
* Optional description
* Content
* Optional actions

Suggested spacing:

```text
Top Padding

↓

Title

space-2

Description

space-4

Content

space-5

Actions

↓

Bottom Padding
```

---

# Forms

Spacing between fields:

```text
space-4
```

Spacing between field groups:

```text
space-6
```

Spacing between form sections:

```text
space-7
```

---

# Lists

Vertical spacing between items:

```text
space-2
```

If items are visually dense (for example, transaction history), reduce to:

```text
space-1
```

---

# Dashboard

Suggested spacing:

Hero Summary

↓

space-7

Command Palette

↓

space-7

Budget Overview

↓

space-7

Charts

↓

space-7

Recent Transactions

↓

space-7

Insights

The dashboard should feel open rather than compressed.

---

# Responsive Behavior

Spacing should reduce gradually on smaller screens.

Desktop:

100%

Tablet:

90%

Mobile:

75–80%

Never remove spacing completely.

Instead, compress proportionally.

---

# Implementation Tokens

Example CSS variables:

```css
:root {
  --space-0: 0px;
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-5: 24px;
  --space-6: 32px;
  --space-7: 48px;
  --space-8: 64px;
  --space-9: 96px;
}
```

Tailwind or any future styling system should map directly to these values.

---

# Rules

Do:

* Use spacing tokens everywhere.
* Maintain consistent rhythm.
* Prefer larger spacing over crowded layouts.

Do not:

* Hardcode pixel values.
* Use inconsistent margins.
* Reduce spacing simply to fit more content.

The solution to overcrowding is better layout—not less whitespace.

---

# Definition of Done

Spacing implementation is complete when:

* Every margin uses a spacing token.
* Every padding uses a spacing token.
* Components follow documented spacing.
* The interface maintains visual rhythm.
* No arbitrary pixel values exist in the codebase.

---

# Closing

Spacing is invisible when done well.

Users rarely notice consistent spacing.

They immediately notice inconsistent spacing.

A calm interface begins with disciplined layout, and disciplined layout begins with a consistent spacing system.
