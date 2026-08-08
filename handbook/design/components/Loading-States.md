---
title: Loading States
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - cards/Base-Card.md
  - Tables.md
  - Empty-States.md
  - ../foundation/Motion.md
  - ../foundation/Spacing.md
  - ../foundation/Colors.md
  - ../foundation/Accessibility.md
---

# Loading States

> **Loading should preserve confidence, not create uncertainty.**

---

# Purpose

Loading States communicate that work is in progress while preserving the structure and context of the interface.

A loading state should reassure users that the application is responsive and that their requested information is being prepared.

Loading should never feel like waiting in the dark.

---

# Design Philosophy

Users should always know:

* Something is happening.
* The application is still responsive.
* Approximately what is loading.

Whenever possible, preserve the final layout while data loads.

---

# Design Principles

Every loading state should:

* Preserve layout stability.
* Avoid unnecessary motion.
* Prevent layout shifts.
* Match the eventual content.
* Transition smoothly into loaded content.

---

# Loading Types

Version 1 supports four loading patterns.

| Pattern          | Usage                            |
| ---------------- | -------------------------------- |
| Skeleton         | Cards, tables, lists             |
| Inline Spinner   | Buttons, small actions           |
| Progress Bar     | Long-running tasks               |
| Full Page Loader | Initial application startup only |

No additional loading patterns should be introduced without updating this specification.

---

# Skeleton Loading

Skeletons are the preferred loading pattern.

Use them for:

* Dashboard cards
* Budget cards
* Insight cards
* Tables
* Settings sections

Skeletons should closely resemble the final layout.

---

# Skeleton Appearance

Skeletons should use:

* Neutral background
* Rounded corners
* Gentle shimmer (optional)

Animation should remain subtle.

Avoid flashy gradients.

---

# Standard Layout Example

```text
┌──────────────────────────────┐
│ ███████████████              │
│                              │
│ ██████████████████████       │
│ ███████████                  │
└──────────────────────────────┘
```

Users should immediately recognize what content is loading.

---

# Inline Spinner

Use only for small, localized actions.

Examples:

* Saving settings
* Importing a file
* Refreshing a widget

Spinners should never replace the entire page.

---

# Progress Bar Loading

Use for operations with measurable progress.

Examples:

* CSV import
* Data export
* Backup

If exact progress is known, use the shared `ProgressBar` component.

---

# Full Page Loading

Reserved exclusively for:

* Initial application launch.
* Critical application initialization.

Avoid full-page loading during normal navigation.

---

# Transition to Loaded State

Loading should transition directly into content.

Avoid:

* Flashing
* Sudden jumps
* Re-rendering entire sections unnecessarily

The interface should feel continuous.

---

# Button Loading

Loading buttons should:

* Preserve width.
* Keep text visible when possible.
* Disable repeated interaction.

Example:

```text
Saving...
```

Do not replace the entire button with a spinner.

---

# Table Loading

Display:

* Table header
* Skeleton rows
* Preserved column widths

Users should understand the table structure before data appears.

---

# Dashboard Loading

Display skeleton versions of:

* Summary Cards
* Budget Cards
* Insight Cards
* Charts

The dashboard layout should remain stable throughout loading.

---

# Charts

Show chart placeholders.

Do not animate chart axes before data is available.

Avoid empty chart frames.

---

# Loading Duration

Guidelines:

| Duration | Recommendation                                |
| -------- | --------------------------------------------- |
| <300ms   | Show no loading indicator                     |
| 300ms–1s | Skeleton or inline spinner                    |
| >1s      | Skeleton plus explanatory text if appropriate |
| >5s      | Offer retry or additional context             |

Avoid showing indicators for extremely brief operations to reduce visual noise.

---

# Accessibility

Loading indicators must:

* Expose appropriate status messages.
* Announce long-running operations.

Example:

```html
role="status"
```

For background updates:

```html
aria-live="polite"
```

Screen readers should understand when loading begins and ends.

---

# Error Recovery

If loading fails:

Replace the loading state with an error state.

Do not leave placeholders visible indefinitely.

Offer a retry action whenever practical.

---

# Responsive Behavior

Skeletons should adapt to screen size in exactly the same way as the final content.

Avoid separate mobile-only loading designs.

---

# Anti-Patterns

Do not:

* Display infinite spinners without explanation.
* Collapse layouts during loading.
* Flash content repeatedly.
* Replace every component with independent spinners.
* Hide the application's structure.

Users should always remain oriented.

---

# Implementation Tokens

```css
--skeleton-radius: var(--radius-md);
--skeleton-gap: var(--space-3);

--loading-animation-duration: 1.2s;

--loading-opacity: 0.12;
```

---

# Definition of Done

A loading implementation is complete when:

* Layout remains stable.
* Appropriate loading patterns are used.
* Accessibility requirements are satisfied.
* Loading transitions smoothly into content.
* Error recovery is handled correctly.

---

# Implementation Notes

### Frontend

* Create reusable components such as `<Skeleton />`, `<LoadingSpinner />`, and `<LoadingOverlay />`.
* Match skeleton dimensions to the final component.
* Avoid unnecessary re-renders when data arrives.

### Backend

* Return partial data where practical to reduce perceived waiting time.
* Include progress information for long-running operations whenever available.

### AI Coding Agent

* Prefer skeletons over full-page spinners.
* Never replace stable layouts with blank screens during loading.
* Use loading indicators proportionate to the duration and scope of the operation.

---

# Future Considerations

Future versions may introduce:

* Streaming data rendering.
* Incremental dashboard updates.
* Predictive preloading.
* Background synchronization indicators.

These enhancements should preserve the same principles of stability, clarity, and responsiveness.

---

# Closing

A loading state is a promise.

It tells users that the application is working on their behalf.

When loading preserves trust and reduces uncertainty, users stop noticing the wait and continue focusing on their task.
