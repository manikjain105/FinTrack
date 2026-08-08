---
title: Elevation
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - ../README.md
  - Colors.md
  - Spacing.md
  - Grid.md
  - ../components/README.md
---

# Elevation

> **Depth should indicate importance, not attract attention.**

---

# Purpose

This document defines the elevation system used throughout FinTrack.

Elevation helps users understand:

* Which elements are interactive.
* Which elements are layered above others.
* Which components require attention.
* How content is visually organized.

Elevation should always communicate hierarchy.

It should never exist purely for decoration.

---

# Design Philosophy

FinTrack embraces a calm and restrained interface.

The majority of the application should appear nearly flat.

Elevation is introduced only when it improves understanding.

Users should rarely notice shadows directly.

Instead, they should naturally perceive visual hierarchy.

---

# Elevation Principles

Every elevation decision should satisfy at least one of the following:

* Indicates interaction.
* Separates layers.
* Improves readability.
* Focuses attention.

If none apply, elevation should not be used.

---

# Elevation Levels

FinTrack defines five standard elevation levels.

| Token       | Purpose                |
| ----------- | ---------------------- |
| elevation-0 | Flat surface           |
| elevation-1 | Cards                  |
| elevation-2 | Hover state            |
| elevation-3 | Dropdowns and Popovers |
| elevation-4 | Dialogs and Modals     |

No additional elevation levels should be introduced without updating this document.

---

# Elevation Tokens

## elevation-0

No visible shadow.

Used for:

* Page backgrounds
* Layout containers
* Navigation backgrounds

---

## elevation-1

Subtle separation.

Used for:

* Cards
* Summary Cards
* Budget Cards
* Chart containers

This should be the most common elevation level.

---

## elevation-2

Interactive emphasis.

Used during:

* Hover
* Active card selection
* Keyboard focus (where appropriate)

The transition from elevation-1 to elevation-2 should feel gentle.

---

## elevation-3

Floating interface elements.

Used for:

* Dropdown menus
* Command suggestions
* Popovers
* Context menus

These elements should clearly appear above surrounding content.

---

## elevation-4

Highest interface layer.

Used for:

* Modals
* Confirmation dialogs
* Critical overlays

Nothing except system-level notifications should appear above this layer.

---

# Shadow Specification

Recommended shadow values:

| Token       | CSS                            |
| ----------- | ------------------------------ |
| elevation-0 | none                           |
| elevation-1 | `0 2px 8px rgba(0,0,0,0.08)`   |
| elevation-2 | `0 6px 16px rgba(0,0,0,0.12)`  |
| elevation-3 | `0 12px 24px rgba(0,0,0,0.16)` |
| elevation-4 | `0 24px 48px rgba(0,0,0,0.24)` |

These values serve as the default implementation and may be refined as the product evolves.

---

# Component Elevation

| Component           | Elevation   |
| ------------------- | ----------- |
| Page Background     | elevation-0 |
| Card                | elevation-1 |
| Summary Card        | elevation-1 |
| Budget Card         | elevation-1 |
| Hovered Card        | elevation-2 |
| Dropdown            | elevation-3 |
| Command Suggestions | elevation-3 |
| Modal               | elevation-4 |
| Confirmation Dialog | elevation-4 |

Components should never define custom shadow values.

---

# Hover Behavior

Interactive surfaces may increase by one elevation level on hover.

Example:

```text
Card
↓

Hover

elevation-1

↓

elevation-2
```

The change should be subtle.

Users should feel interaction rather than notice animation.

---

# Focus Behavior

Keyboard focus should be communicated primarily through:

* Focus ring.
* Border.
* Color.

Elevation alone must never indicate focus.

---

# Dark Theme Considerations

Heavy shadows lose effectiveness on dark surfaces.

For Version 1:

* Prefer softer shadows.
* Increase separation through surface color where necessary.
* Avoid excessively dark shadows.

Depth should feel natural rather than dramatic.

---

# Layer Order

Visual stacking order:

1. Background
2. Content
3. Cards
4. Dropdowns
5. Drawers
6. Modals
7. Toasts

This hierarchy should remain consistent across the application.

---

# Borders vs Elevation

Prefer borders when:

* Separating adjacent sections.
* Creating subtle distinction.
* Defining table structure.

Prefer elevation when:

* Creating floating surfaces.
* Indicating interaction.
* Establishing overlay hierarchy.

Do not combine heavy borders and heavy shadows.

---

# Accessibility

Shadows should never be the only indication of depth.

Use:

* Surface color.
* Borders.
* Spacing.
* Layering.

Users with reduced vision should still understand hierarchy.

---

# Implementation Tokens

Example CSS variables:

```css
:root {
  --shadow-none: none;
  --shadow-sm: 0 2px 8px rgba(0,0,0,0.08);
  --shadow-md: 0 6px 16px rgba(0,0,0,0.12);
  --shadow-lg: 0 12px 24px rgba(0,0,0,0.16);
  --shadow-xl: 0 24px 48px rgba(0,0,0,0.24);
}
```

Components should consume these tokens rather than defining their own shadows.

---

# Rules

Do:

* Use documented elevation tokens.
* Increase elevation only when hierarchy changes.
* Keep shadows subtle.

Do not:

* Create custom shadow values.
* Stack multiple shadows without justification.
* Use elevation to decorate static content.

---

# Definition of Done

An interface satisfies the elevation system when:

* All shadows reference elevation tokens.
* Layer hierarchy is consistent.
* Interactive states use predictable depth.
* Overlays appear above surrounding content.
* No component introduces undocumented shadow values.

---

# Implementation Notes

### Frontend

* Expose elevation values as CSS custom properties.
* Map elevation tokens to the Tailwind theme configuration.
* Prefer transitions of `150–200ms` when changing elevation.

### Backend

* Not applicable.

### AI Coding Agent

* Never hardcode box-shadow values.
* Always consume elevation tokens.
* Do not introduce new elevation levels without updating this handbook.

---

# Closing

Elevation is not about making elements stand out.

It is about helping users understand where they are, what they can interact with, and what deserves their attention.

When used consistently, depth becomes invisible—and that is exactly the goal.
