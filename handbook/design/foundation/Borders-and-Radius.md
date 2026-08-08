---
title: Borders and Radius
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - ../README.md
  - Colors.md
  - Spacing.md
  - ../components/README.md
---

# Borders and Radius

> **Borders define structure. Radius defines personality.**

---

# Purpose

This document defines the border system and corner radius tokens used throughout FinTrack.

Every border, divider, outline and rounded corner in the application must use the tokens defined here.

No component should introduce its own border widths or radius values.

---

# Design Philosophy

Borders should quietly separate.

Radius should soften.

Neither should become decorative.

Users should feel structure—not notice it.

---

# Border Principles

Borders exist to:

* Separate information.
* Define interaction areas.
* Improve readability.
* Support accessibility.

Borders should never become the dominant visual element.

---

# Border Width Tokens

| Token    | Value | Usage         |
| -------- | ----: | ------------- |
| border-0 |   0px | No border     |
| border-1 |   1px | Default       |
| border-2 |   2px | Focus         |
| border-4 |   4px | Rare emphasis |

Only these border widths are permitted.

---

# Border Color Tokens

Always reference semantic colors.

| Token          | Purpose                    |
| -------------- | -------------------------- |
| border-default | Standard component borders |
| border-muted   | Low emphasis               |
| border-focus   | Keyboard focus             |
| border-success | Positive validation        |
| border-warning | Budget nearing limit       |
| border-danger  | Errors                     |

Components must never hardcode border colors.

---

# Corner Radius Philosophy

Radius communicates friendliness.

Too little radius feels rigid.

Too much radius feels playful.

FinTrack should feel modern, calm and professional.

---

# Radius Tokens

| Token       |  Value | Usage                 |
| ----------- | -----: | --------------------- |
| radius-none |    0px | Tables                |
| radius-sm   |    6px | Badges                |
| radius-md   |   10px | Inputs                |
| radius-lg   |   12px | Buttons               |
| radius-xl   |   16px | Cards                 |
| radius-2xl  |   20px | Large panels          |
| radius-full | 9999px | Chips, avatars, pills |

These values apply consistently throughout the application.

---

# Component Mapping

| Component       | Radius      |
| --------------- | ----------- |
| Button          | radius-lg   |
| Input           | radius-md   |
| Command Palette | radius-xl   |
| Card            | radius-xl   |
| Budget Card     | radius-xl   |
| Toast           | radius-lg   |
| Modal           | radius-2xl  |
| Dropdown        | radius-lg   |
| Badge           | radius-sm   |
| Chip            | radius-full |

No custom radius values should be introduced.

---

# Dividers

Dividers should:

* Use `border-default`.
* Be 1px thick.
* Extend only as far as necessary.

Avoid decorative separators.

Whitespace is usually a better separator than a line.

---

# Focus Rings

Focus should be visible without relying on color alone.

Specification:

* Width: border-2
* Offset: 2px
* Color: border-focus

Focus indicators must remain visible in both light and dark themes.

---

# Validation States

Input validation uses borders and supporting text.

| State   | Border         |
| ------- | -------------- |
| Default | border-default |
| Success | border-success |
| Warning | border-warning |
| Error   | border-danger  |

Icons may reinforce the state but should not replace text.

---

# Tables

Tables should use:

* 1px row dividers.
* No vertical borders.
* Clear spacing between rows.

Avoid heavy gridlines.

---

# Cards

Cards use:

* radius-xl
* border-1
* border-default

Borders should remain subtle.

Elevation, spacing and layout should carry most of the visual hierarchy.

---

# Anti-Patterns

Do not:

* Mix multiple border widths within the same component.
* Combine thick borders with heavy shadows.
* Introduce random corner radius values.
* Use borders where whitespace is sufficient.
* Remove focus outlines without replacing them.

---

# Implementation Tokens

Example CSS variables:

```css
:root {
  --border-0: 0px;
  --border-1: 1px;
  --border-2: 2px;
  --border-4: 4px;

  --radius-none: 0px;
  --radius-sm: 6px;
  --radius-md: 10px;
  --radius-lg: 12px;
  --radius-xl: 16px;
  --radius-2xl: 20px;
  --radius-full: 9999px;
}
```

All components should consume these tokens.

---

# Accessibility

Borders alone should never communicate state.

Every validation state must also include:

* Supporting text.
* Appropriate iconography (where applicable).
* Screen reader announcements for critical errors.

---

# Definition of Done

Border implementation is complete when:

* All border widths use documented tokens.
* All radii use documented tokens.
* Focus indicators are keyboard accessible.
* No hardcoded border styles remain.
* Components maintain consistent visual hierarchy.

---

# Implementation Notes

### Frontend

* Expose border and radius values as design tokens.
* Map tokens directly into the Tailwind theme.
* Use semantic border colors instead of raw hex values.

### Backend

* Not applicable.

### AI Coding Agent

* Never hardcode `border-radius`.
* Never introduce undocumented border widths.
* Always use semantic border colors.

---

# Future Considerations

Future versions may add:

* Brand-specific themes.
* High-contrast accessibility themes.
* User-selectable interface density.

These additions must continue using the same border and radius token system.

---

# Closing

Borders should create structure.

Radius should create comfort.

Together they shape the personality of FinTrack without demanding attention.

The best border system is the one users never consciously notice.
