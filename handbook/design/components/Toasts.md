---
title: Toasts
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - Application-Shell.md
  - Buttons.md
  - ../foundation/Colors.md
  - ../foundation/Typography.md
  - ../foundation/Spacing.md
  - ../foundation/Borders-and-Radius.md
  - ../foundation/Elevation.md
  - ../foundation/Motion.md
---

# Toasts

> **Feedback should reassure users without interrupting them.**

---

# Purpose

Toasts provide lightweight, non-blocking feedback for completed actions.

They confirm success, communicate warnings, surface recoverable errors, and occasionally present an immediate follow-up action.

Toasts should never interrupt the user's workflow.

---

# Design Philosophy

A toast is acknowledgement—not conversation.

Users should immediately understand:

* What happened.
* Whether they need to act.
* Whether they can safely continue.

If the answer is "nothing else is required", the toast should disappear automatically.

---

# Design Principles

Every toast should:

* Be concise.
* Be contextual.
* Be dismissible (when appropriate).
* Never obscure important content.
* Never require unnecessary interaction.

---

# Supported Toast Types

Version 1 supports exactly four toast types.

| Type        | Purpose                       |
| ----------- | ----------------------------- |
| Success     | Action completed successfully |
| Information | Informational update          |
| Warning     | Attention required soon       |
| Error       | Recoverable problem           |

No additional toast types should be introduced without updating this specification.

---

# Standard Layout

```text
┌────────────────────────────────────────────┐
│ ✓ Transaction saved                        │
│ Saved ₹420 to Food                         │
│                              Undo          │
└────────────────────────────────────────────┘
```

---

# Anatomy

A toast consists of:

* Status icon
* Title
* Optional description
* Optional action
* Optional dismiss button

The title is required.

---

# Placement

Desktop:

Bottom-right corner.

Mobile:

Bottom-center.

Toasts should appear above page content but below modal dialogs.

---

# Stack Behavior

Maximum visible toasts:

```text
3
```

If more than three toasts are queued:

* Display the newest toast.
* Queue the remainder.
* Remove the oldest visible toast first.

---

# Width

Desktop:

Minimum:

```text
320px
```

Maximum:

```text
420px
```

Mobile:

Fill available width with standard page margins.

---

# Duration

| Type        |                   Duration |
| ----------- | -------------------------: |
| Success     |                  4 seconds |
| Information |                  5 seconds |
| Warning     | Persistent until dismissed |
| Error       | Persistent until dismissed |

Persistent toasts should never disappear automatically.

---

# Animation

Entrance:

* Fade in.
* Slight upward translation.

Exit:

* Fade out.

Duration:

```text
200ms
```

Do not use bounce, rotation, or scaling effects.

---

# Content Guidelines

## Success

Examples:

* Transaction saved.
* Budget updated.
* Export completed.

---

## Information

Examples:

* Data imported.
* Exchange rates updated.
* Backup completed.

---

## Warning

Examples:

* Monthly budget nearly reached.
* Import contains duplicate entries.

Warnings should suggest the next step.

---

## Error

Examples:

* Unable to save transaction.
* Export failed.
* Database unavailable.

Errors should explain the issue without exposing technical details.

---

# Actions

Toasts may include exactly one secondary action.

Recommended examples:

* Undo
* Retry
* View

Avoid multiple buttons.

Primary workflows should never depend on toast actions.

---

# Undo

Undo is the preferred recovery mechanism for reversible actions.

Example:

```text
Transaction saved.

Undo
```

Undo remains available only while the toast is visible.

Avoid confirmation dialogs when Undo is sufficient.

---

# Dismissal

Users may dismiss any toast manually.

Dismiss buttons should appear only on:

* Warning
* Error

Success and Information toasts may omit the dismiss button.

---

# Color Rules

Use semantic color tokens.

| Type        | Token   |
| ----------- | ------- |
| Success     | Success |
| Information | Info    |
| Warning     | Warning |
| Error       | Danger  |

Background surfaces remain neutral.

Color should emphasize status—not dominate the component.

---

# Icons

Recommended icons:

| Type        | Icon          |
| ----------- | ------------- |
| Success     | CircleCheck   |
| Information | Info          |
| Warning     | TriangleAlert |
| Error       | CircleAlert   |

Icons support recognition but never replace text.

---

# Accessibility

Every toast must:

* Announce itself to screen readers.
* Receive an appropriate live region.

Success and information:

```html
aria-live="polite"
```

Warnings and errors:

```html
aria-live="assertive"
```

Do not automatically move keyboard focus to a toast.

---

# Responsive Behavior

Desktop:

Bottom-right stack.

Tablet:

Bottom-right stack.

Mobile:

Bottom-center.

Spacing should remain consistent with the design token system.

---

# Anti-Patterns

Do not:

* Show multiple success toasts for one action.
* Display technical error messages.
* Block interaction with toasts.
* Use modal dialogs for routine confirmations.
* Require users to dismiss success messages.

---

# Implementation Tokens

```css
--toast-width-min: 320px;
--toast-width-max: 420px;

--toast-radius: var(--radius-lg);
--toast-padding: var(--space-4);

--toast-gap: var(--space-3);

--toast-shadow: var(--shadow-lg);

--toast-animation: var(--motion-normal);
```

---

# Definition of Done

A toast implementation is complete when:

* It follows the documented layout.
* Uses semantic color tokens.
* Supports stacking.
* Meets accessibility requirements.
* Provides non-blocking feedback.
* Handles Undo where appropriate.

---

# Implementation Notes

### Frontend

* Implement a global `<ToastProvider />`.
* Expose a simple API:

```ts
toast.success(...)
toast.info(...)
toast.warning(...)
toast.error(...)
```

* Queue additional toasts automatically.

### Backend

* Not applicable.

### AI Coding Agent

* Never use alert dialogs for routine feedback.
* Prefer Undo over confirmation for reversible actions.
* Keep toast messages short, factual, and action-oriented.

---

# Future Considerations

Future versions may introduce:

* Rich toasts with progress indicators.
* Download progress notifications.
* Background synchronization status.
* Cross-device sync notifications.

These additions should preserve the lightweight, non-blocking nature of the toast system.

---

# Closing

A successful toast disappears before users think about dismissing it.

It quietly confirms that the application understood their intent and completed the requested action, allowing them to continue without interruption.
