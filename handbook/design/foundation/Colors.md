---
title: Colors
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - ../README.md
  - Design-Principles.md
  - ../../foundation/Manifesto.md
---

# Color System

> **Color communicates meaning, not decoration.**

---

# Purpose

This document defines the complete color system for FinTrack.

Colors should guide attention, communicate state, and improve comprehension.

Color should never be used simply because it looks attractive.

---

# Design Philosophy

Most of the interface should feel neutral.

Important information should stand out because it is meaningful—not because every element is colorful.

A user should immediately understand:

* what is actionable,
* what is informational,
* what is positive,
* what is negative,
* what requires attention.

---

# Color Principles

## Neutral First

The interface should primarily consist of neutral colors.

This allows meaningful colors to draw attention naturally.

---

## Meaning Before Branding

Every color must have a purpose.

If removing a color changes nothing, that color should not exist.

---

## Consistency

A semantic meaning should always use the same color.

Examples:

Success is always green.

Errors are always red.

Warnings are always amber.

Never swap meanings across screens.

---

# Semantic Color Tokens

The design system uses semantic tokens instead of hardcoded color names.

| Token          | Purpose                            |
| -------------- | ---------------------------------- |
| Primary        | Brand identity and primary actions |
| Success        | Positive outcomes                  |
| Warning        | Approaching limits                 |
| Danger         | Errors and exceeded budgets        |
| Info           | Informational messages             |
| Surface        | Cards and panels                   |
| Background     | Application background             |
| Border         | Dividers and outlines              |
| Text Primary   | Main content                       |
| Text Secondary | Supporting content                 |
| Text Muted     | Low-emphasis information           |

Application components should reference these tokens only.

---

# Suggested Palette

> These values define the initial implementation and may evolve over time.

| Token          | Hex     |
| -------------- | ------- |
| Primary        | #2563EB |
| Success        | #16A34A |
| Warning        | #F59E0B |
| Danger         | #DC2626 |
| Info           | #0EA5E9 |
| Background     | #0F172A |
| Surface        | #1E293B |
| Border         | #334155 |
| Text Primary   | #F8FAFC |
| Text Secondary | #CBD5E1 |
| Text Muted     | #94A3B8 |

---

# Financial Meaning

FinTrack assigns consistent meanings to financial states.

## Positive

Used for:

* Savings
* Budget remaining
* Income
* Successful actions

Token:

Success

---

## Caution

Used for:

* Budget approaching limit
* Missing information
* Recommendations

Token:

Warning

---

## Negative

Used for:

* Overspending
* Validation errors
* Failed operations
* Budget exceeded

Token:

Danger

---

# Charts

Charts should remain restrained.

Recommended maximum:

* Five distinct category colors.

If additional categories exist, reuse neutral shades rather than introducing unrelated colors.

Charts should prioritize readability over variety.

---

# Progress Indicators

Budget progress should communicate status through color.

| Status | Color   |
| ------ | ------- |
| 0–79%  | Success |
| 80–99% | Warning |
| 100%+  | Danger  |

This mapping should remain consistent throughout the application.

---

# Buttons

| Button Type    | Token   |
| -------------- | ------- |
| Primary        | Primary |
| Secondary      | Surface |
| Destructive    | Danger  |
| Success Action | Success |

No component should define custom button colors.

---

# Notifications

| Notification | Token   |
| ------------ | ------- |
| Success      | Success |
| Warning      | Warning |
| Error        | Danger  |
| Information  | Info    |

Toast messages, alerts, and banners must use these mappings.

---

# Accessibility

All color combinations must satisfy WCAG AA contrast requirements at a minimum.

Color must never be the only indicator of meaning.

Examples:

✔ Green icon + "Saved"

✔ Red icon + "Budget exceeded"

Avoid relying on color alone.

---

# Dark Mode

Version 1 is designed primarily for a dark interface.

Dark surfaces should feel soft rather than pure black.

Avoid:

* #000000 backgrounds
* Extremely saturated colors
* High-contrast borders

Use layered surfaces to establish hierarchy.

---

# Future Theme Support

The semantic token system should allow:

* Light theme
* High-contrast theme
* Seasonal themes
* Custom user themes

without requiring component changes.

Only token definitions should change.

---

# Implementation Rule

Components must never reference raw hex values directly.

Incorrect:

```css
color: #16A34A;
```

Correct:

```css
color: var(--color-success);
```

All colors should be exposed through design tokens.

---

# Definition of Done

A screen is considered complete when:

* All colors come from semantic tokens.
* Financial states use consistent meanings.
* Contrast requirements are satisfied.
* No hardcoded colors remain.
* Charts remain readable and restrained.

---

# Closing

The best color system is one users rarely notice.

Its purpose is not to decorate the interface.

Its purpose is to quietly guide attention, reinforce meaning, and build trust through consistency.
