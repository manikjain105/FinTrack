---
title: Progress Bars
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - cards/Base-Card.md
  - cards/Budget-Card.md
  - ../foundation/Colors.md
  - ../foundation/Borders-and-Radius.md
  - ../foundation/Motion.md
  - ../foundation/Spacing.md
---

# Progress Bars

> **Progress Bars communicate completion—not decoration.**

---

# Purpose

The Progress Bar component visualizes progress toward a measurable goal.

In FinTrack, Progress Bars primarily communicate:

* Budget utilization
* Savings goal progress
* Import progress
* Export progress
* Background task completion

Progress Bars should always represent measurable values.

They must never be used as decorative elements.

---

# Design Philosophy

A Progress Bar should answer one question:

> **"How far along am I?"**

Users should understand progress instantly.

The exact percentage is secondary to the overall visual impression.

---

# Component Responsibilities

The Progress Bar is responsible for displaying:

* Current value
* Maximum value
* Progress percentage
* Visual status

It is **not** responsible for:

* Budget calculations
* Forecasting
* Financial interpretation
* Trend analysis

Those responsibilities belong to higher-level components.

---

# Standard Specifications

| Property      |                  Value |
| ------------- | ---------------------: |
| Height        |                    8px |
| Border Radius |            radius-full |
| Track Color   | Border / Muted Surface |
| Fill Color    |         Semantic Token |
| Animation     |          motion-normal |

These values apply to every Progress Bar implementation.

---

# Anatomy

```text
┌────────────────────────────────────────────┐
│ ███████████████░░░░░░░░░░░░░░░░░░░░░░░░░░ │
└────────────────────────────────────────────┘

61%
```

The component consists of:

* Track
* Fill
* Optional percentage label

---

# Variants

Version 1 supports four variants.

## Budget

Represents budget utilization.

Most common usage.

---

## Goal

Represents progress toward a target.

Example:

Emergency Fund

---

## Task

Represents application processes.

Examples:

Import

Export

Backup

---

## Determinate

Represents measurable completion.

Requires:

* Current value
* Maximum value

---

# Indeterminate

Used only when completion cannot be calculated.

Examples:

* Initial synchronization
* Database migration

Indeterminate Progress Bars should be used sparingly.

---

# Color Mapping

Progress Bars use semantic colors.

| Status  | Token   |
| ------- | ------- |
| Success | Success |
| Warning | Warning |
| Danger  | Danger  |
| Neutral | Primary |

The track always uses a muted neutral color.

---

# Budget Thresholds

Standard thresholds:

| Percentage | Status  |
| ---------- | ------- |
| 0–79%      | Success |
| 80–99%     | Warning |
| 100%+      | Danger  |

These thresholds must remain consistent throughout FinTrack.

---

# Labels

Progress Bars may optionally display:

```text
61%

₹18,420 / ₹30,000

18 of 30 days
```

Labels should remain concise.

Avoid long descriptive sentences.

---

# Animation

Progress updates should animate smoothly.

Duration:

```text
200ms
```

Animation should occur only when values change.

Do not replay animations every time the page loads.

---

# Accessibility

Every Progress Bar must expose:

* Current value
* Maximum value
* Percentage
* Accessible label

Example:

> Budget utilization. 61 percent complete.

Use:

```html
role="progressbar"
```

Include:

* `aria-valuemin`
* `aria-valuemax`
* `aria-valuenow`

---

# Responsive Behavior

The Progress Bar always expands to fill the available width.

Height remains constant across devices.

Only width should adapt.

---

# Anti-Patterns

Do not:

* Animate continuously.
* Flash warning colors.
* Use gradients.
* Add decorative textures.
* Stack multiple Progress Bars without context.

One clear Progress Bar is better than several competing indicators.

---

# Empty State

If no progress exists:

Display:

```text
0%
```

Do not hide the component.

---

# Error State

If progress cannot be calculated:

Hide the Progress Bar and display an explanatory message.

Never display inaccurate percentages.

---

# Implementation Tokens

```css
--progress-height: 8px;
--progress-radius: var(--radius-full);

--progress-success: var(--color-success);
--progress-warning: var(--color-warning);
--progress-danger: var(--color-danger);
--progress-track: var(--color-border);
```

---

# Definition of Done

A Progress Bar implementation is complete when:

* It uses documented design tokens.
* Progress values are accurate.
* Semantic colors are applied consistently.
* Accessibility requirements are satisfied.
* Animation follows the motion specification.

---

# Implementation Notes

### Frontend

* Implement a reusable `<ProgressBar />` component.
* Accept props such as `value`, `max`, `variant`, `status`, and `showLabel`.
* Clamp values to prevent rendering errors while still allowing percentages above 100% to be represented appropriately by the parent component.

### Backend

* Return normalized values where practical.
* Avoid embedding presentation logic in API responses.

### AI Coding Agent

* Never create custom progress indicators.
* Always reuse the shared Progress Bar component.
* Keep business logic outside the component.

---

# Future Considerations

Future versions may introduce:

* Circular progress indicators.
* Goal milestone markers.
* Forecast overlays.
* Comparative progress (current vs previous period).

These additions should extend the existing component rather than replace it.

---

# Closing

A Progress Bar should communicate progress in a fraction of a second.

Users should understand whether they are on track before they read a single number.

That clarity—not animation—is the purpose of this component.
