---
title: Buttons
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - ../README.md
  - ../foundation/Colors.md
  - ../foundation/Typography.md
  - ../foundation/Spacing.md
  - ../foundation/Borders-and-Radius.md
  - ../foundation/Elevation.md
  - ../foundation/Motion.md
  - ../foundation/Icons.md
---

# Buttons

> **Buttons represent commitment. Every click should feel intentional.**

---

# Purpose

This document defines every button used throughout FinTrack.

Buttons initiate user actions.

They should clearly communicate:

* what will happen,
* whether the action is available,
* and the importance of the action.

Buttons must never surprise the user.

---

# Design Principles

Buttons should be:

* Obvious
* Accessible
* Predictable
* Fast
* Consistent

Every button should answer one question:

> **"What happens if I click this?"**

If the answer isn't obvious, rewrite the label.

---

# Standard Specifications

| Property           |     Value |
| ------------------ | --------: |
| Height             |      44px |
| Border Radius      | radius-lg |
| Horizontal Padding |   space-4 |
| Vertical Padding   |   space-2 |
| Font               |      Body |
| Font Weight        |       600 |
| Icon Size          |   icon-md |

---

# Button Variants

Version 1 supports exactly five variants.

## Primary

Purpose:

The most important action on a screen.

Examples:

* Add Transaction
* Save Changes
* Import Data

Only one primary button should appear within a logical section.

---

## Secondary

Purpose:

Alternative actions.

Examples:

* Cancel
* Export
* View Details

Secondary buttons should never compete visually with the primary action.

---

## Ghost

Purpose:

Low-emphasis actions.

Examples:

* Edit
* Show More
* Retry

Ghost buttons rely on text and hover feedback rather than filled backgrounds.

---

## Destructive

Purpose:

Irreversible actions.

Examples:

* Delete Transaction
* Reset Data

Destructive buttons must use the Danger semantic token.

---

## Icon Button

Purpose:

Compact actions where the surrounding context already explains intent.

Examples:

* Edit
* Delete
* Close
* Filter

Icon buttons must always include an accessible label.

---

# Sizes

Only three button sizes are permitted.

| Size   | Height |
| ------ | -----: |
| Small  |   36px |
| Medium |   44px |
| Large  |   52px |

Medium is the default throughout the application.

---

# States

Every button supports these states:

* Default
* Hover
* Focus
* Active
* Disabled
* Loading

No custom states should be introduced.

---

# Hover

Changes allowed:

* Background
* Border
* Elevation

Duration:

150ms

Buttons should feel responsive without drawing attention.

---

# Focus

Focus must include:

* Visible focus ring
* Keyboard accessibility
* High-contrast outline

Focus should never rely solely on color.

---

# Active

The pressed state should feel immediate.

Avoid dramatic scaling or bounce effects.

---

# Disabled

Disabled buttons should:

* Remain readable
* Reduce emphasis
* Ignore pointer interaction

Never reduce opacity below 40%.

---

# Loading

Loading buttons should:

* Preserve width
* Replace the icon (or append) with a spinner
* Disable repeated clicks

Button text should remain visible whenever possible.

Example:

```text
Saving...
```

Avoid layout shifts while loading.

---

# Labels

Use clear action-oriented language.

Good:

* Save
* Add Transaction
* Export CSV
* Import Data
* Delete

Avoid:

* Submit
* Continue
* Proceed
* Confirm

Labels should describe the outcome.

---

# Icons

Icons are optional.

When present:

* Place before the label for forward actions.
* Place after the label only when indicating direction (for example, "Next →").

Spacing:

Use `space-2` between icon and text.

---

# Accessibility

Buttons must support:

* Keyboard activation (`Enter` and `Space`)
* Screen readers
* Visible focus state
* Touch targets of at least 44×44px

Interactive icon buttons require an `aria-label`.

---

# Responsive Rules

Button height remains consistent across devices.

On mobile:

* Prefer full-width buttons in forms.
* Keep primary actions within easy thumb reach.

---

# Anti-Patterns

Do not:

* Use more than one primary button within a section.
* Create custom button colors.
* Invent additional button variants.
* Use icons without accessible labels.
* Disable buttons without explaining why.

---

# Example Mapping

| Action             | Variant     |
| ------------------ | ----------- |
| Add Transaction    | Primary     |
| Save Settings      | Primary     |
| Export Data        | Secondary   |
| Cancel             | Ghost       |
| Delete Transaction | Destructive |
| Edit               | Icon Button |

---

# Implementation Tokens

```css
--button-height-sm: 36px;
--button-height-md: 44px;
--button-height-lg: 52px;

--button-radius: var(--radius-lg);
--button-padding-x: var(--space-4);
--button-padding-y: var(--space-2);
```

---

# Definition of Done

A button implementation is complete when:

* It uses documented design tokens.
* All interaction states are implemented.
* Keyboard interaction works correctly.
* Accessibility requirements are satisfied.
* Visual behavior matches this specification.

---

# Implementation Notes

### Frontend

* Build a single reusable `<Button />` component.
* Implement variants using a variant system (for example, `variant="primary"`).
* Centralize styles to prevent duplication.

### Backend

* Not applicable.

### AI Coding Agent

* Never create custom button styles.
* Always use the shared Button component.
* Add new variants only by updating this handbook first.

---

# Future Considerations

Future versions may introduce:

* Split buttons
* Dropdown buttons
* Floating action buttons (only if a clear product need emerges)

These additions must remain consistent with the existing interaction model.

---

# Closing

Buttons represent decisions.

Every button should make users feel confident about what happens next.

When users stop thinking about the interface and simply act, the button system has succeeded.
