---
title: Motion
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - ../README.md
  - Design-Principles.md
  - ../components/README.md
  - Elevation.md
  - Responsive.md
---

# Motion

> **Motion communicates change. It never exists for decoration.**

---

# Purpose

This document defines the motion system used throughout FinTrack.

Motion should help users understand:

* What changed.
* Where something moved.
* What requires attention.
* Whether an action succeeded.
* How interfaces transition between states.

Motion should always improve comprehension.

If removing an animation improves clarity, remove it.

---

# Motion Principles

Every animation must satisfy at least one of these goals:

* Explain change.
* Confirm an action.
* Guide attention.
* Preserve spatial awareness.
* Reduce perceived waiting time.

If none apply, do not animate.

---

# Motion Characteristics

The FinTrack motion language should feel:

* Calm
* Fast
* Natural
* Predictable
* Purposeful

Avoid:

* Bouncy animations
* Elastic effects
* Flashing elements
* Dramatic scaling
* Long transitions

The interface should feel responsive rather than playful.

---

# Timing Tokens

| Token          | Duration | Usage             |
| -------------- | -------: | ----------------- |
| motion-instant |      0ms | Immediate changes |
| motion-fast    |    150ms | Hover, focus      |
| motion-normal  |    200ms | Cards, buttons    |
| motion-medium  |    250ms | Panels, drawers   |
| motion-slow    |    300ms | Page transitions  |

Animations longer than **300ms** require documented justification.

---

# Easing

Use only three easing curves.

| Token         | CSS      |
| ------------- | -------- |
| ease-standard | ease     |
| ease-in       | ease-in  |
| ease-out      | ease-out |

Avoid custom cubic-bezier curves unless the interaction specifically benefits from them.

---

# Standard Transitions

## Hover

Duration:

```text
150ms
```

Properties:

* Background
* Border
* Shadow
* Color

---

## Focus

Duration:

```text
150ms
```

Focus should primarily rely on:

* Focus ring
* Border
* Color

Motion is secondary.

---

## Button Press

Duration:

```text
100ms
```

The interaction should feel immediate.

Avoid noticeable delays.

---

## Card Hover

Transition:

* Elevation
* Border
* Background

Duration:

```text
200ms
```

Cards should never "jump."

---

# Command Palette

When a transaction is successfully added:

1. Input clears.
2. Success toast appears.
3. Dashboard updates.
4. Charts refresh.

These transitions should feel like one continuous interaction rather than separate events.

---

# Toast Notifications

Entrance:

Fade + slight upward movement.

Exit:

Fade only.

Maximum display time:

```text
4 seconds
```

Users should never dismiss success toasts manually.

---

# Modal

Opening:

* Fade overlay.
* Scale content from 98% → 100%.

Closing:

* Reverse animation.

Duration:

```text
250ms
```

Avoid dramatic zoom effects.

---

# Drawer

Direction:

Slide from edge.

Duration:

```text
250ms
```

The drawer should preserve spatial awareness by clearly indicating where it originated.

---

# Charts

Charts should animate only when data changes.

Examples:

* Bar height transitions.
* Line interpolation.
* Donut segment updates.

Duration:

```text
250ms
```

Do not replay animations every time the page loads.

---

# Loading States

Prefer:

* Skeletons
* Progressive rendering

Avoid:

* Full-page spinners
* Blocking overlays

The layout should remain stable while content loads.

---

# Empty States

Do not animate empty state illustrations.

A calm interface should not distract users when no data exists.

---

# Error States

Error messages should:

* Appear quickly.
* Fade naturally.
* Never shake the interface.

Avoid aggressive error animations.

---

# Reduced Motion

Respect the user's operating system preference.

When reduced motion is enabled:

* Disable non-essential animations.
* Remove scaling.
* Remove sliding.
* Keep only opacity transitions where necessary.

Accessibility always takes precedence over aesthetics.

---

# Motion Hierarchy

Order of importance:

1. User action feedback.
2. Navigation.
3. Data updates.
4. Hover interactions.
5. Decorative effects.

Decorative effects should always have the lowest priority.

---

# Motion Tokens

Example CSS variables:

```css
:root {
  --motion-fast: 150ms;
  --motion-normal: 200ms;
  --motion-medium: 250ms;
  --motion-slow: 300ms;

  --ease-standard: ease;
  --ease-in: ease-in;
  --ease-out: ease-out;
}
```

---

# Rules

Do:

* Animate state changes.
* Keep transitions short.
* Maintain consistency.
* Respect reduced-motion preferences.

Do not:

* Animate every element.
* Chain unnecessary animations.
* Delay user interactions.
* Use motion purely for decoration.

---

# Definition of Done

Motion implementation is complete when:

* All durations use documented tokens.
* Animations communicate state changes.
* Reduced-motion preferences are respected.
* Motion remains consistent across all components.
* No undocumented animations exist.

---

# Implementation Notes

### Frontend

* Expose motion durations and easing curves as design tokens.
* Use CSS transitions for simple interactions.
* Reserve JavaScript animations for complex data visualizations only.

### Backend

* Not applicable.

### AI Coding Agent

* Never introduce custom animation timings.
* Reuse motion tokens across all components.
* Prefer subtle opacity and elevation changes over large transforms.

---

# Future Considerations

Future versions may introduce:

* Shared element transitions.
* Advanced chart animations.
* Page transition choreography.

These additions must preserve the calm interaction style established in Version 1.

---

# Closing

The best motion is rarely noticed.

Users should never think:

*"That animation was beautiful."*

They should think:

*"That felt natural."*

When motion quietly improves understanding without drawing attention to itself, it has achieved its purpose.
