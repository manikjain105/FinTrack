---
title: Modals
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
  - ../foundation/Accessibility.md
---

# Modals

> **A modal should interrupt only when interruption is justified.**

---

# Purpose

Modals temporarily interrupt the current workflow to request a decision, present important information, or collect focused input.

Because they block interaction with the rest of the application, they should be used sparingly.

Whenever a workflow can be completed inline, it should be.

---

# Design Philosophy

A modal should never surprise the user.

When it appears, the user should immediately understand:

* Why it appeared.
* What decision is required.
* What will happen next.

Every modal should help users complete one focused task.

---

# Design Principles

Every modal should:

* Have a single purpose.
* Be easy to dismiss when appropriate.
* Preserve user context.
* Avoid unnecessary complexity.
* Support keyboard-only interaction.

---

# Appropriate Use Cases

Version 1 uses modals for:

* Confirming destructive actions.
* Editing complex data.
* Import previews.
* Export options.
* Viewing detailed transaction information.

Avoid using modals for routine data entry.

---

# Do Not Use Modals For

* Success messages.
* Simple confirmations that Undo can handle.
* Navigation.
* Tooltips.
* Notifications.
* Onboarding.

Prefer inline interfaces whenever possible.

---

# Standard Layout

```text
┌────────────────────────────────────────────┐
│ Delete Transaction                         │
│                                            │
│ This action cannot be undone.              │
│                                            │
│ Cancel                    Delete           │
└────────────────────────────────────────────┘
```

---

# Anatomy

Every modal contains:

* Title (required)
* Body content
* Primary action
* Secondary action
* Close button (optional)

The title should clearly describe the task.

---

# Modal Sizes

Version 1 supports four sizes.

| Size        |         Width |
| ----------- | ------------: |
| Small       |         400px |
| Medium      |         600px |
| Large       |         800px |
| Full Screen | 100% viewport |

Default:

```text
Medium
```

---

# Height

Modals should size to their content.

Avoid fixed heights unless scrolling is unavoidable.

When scrolling is required:

* Header remains fixed.
* Footer remains fixed.
* Only content scrolls.

---

# Overlay

The overlay should:

* Dim the background.
* Prevent interaction with underlying content.
* Preserve context.

Background content should remain visible but visually de-emphasized.

---

# Primary Action

Exactly one primary action.

Examples:

* Save
* Delete
* Import
* Export

The primary action should always be visually dominant.

---

# Secondary Action

Examples:

* Cancel
* Close
* Back

Secondary actions should never compete with the primary action.

---

# Close Behavior

Users may close a modal using:

* Escape
* Close button
* Cancel button
* Overlay click (where appropriate)

Destructive confirmation dialogs should not close on accidental overlay clicks.

---

# Focus Management

When opened:

* Focus moves to the modal.

When closed:

* Focus returns to the triggering element.

Keyboard users should never lose context.

---

# Keyboard Support

Required shortcuts:

| Shortcut    | Action                            |
| ----------- | --------------------------------- |
| Esc         | Close (if permitted)              |
| Tab         | Next focusable element            |
| Shift + Tab | Previous focusable element        |
| Enter       | Primary action (when appropriate) |

Keyboard focus must remain trapped inside the modal until it closes.

---

# Accessibility

Every modal must include:

```html
role="dialog"
```

For destructive confirmations:

```html
aria-modal="true"
```

The modal must expose:

* Accessible title.
* Accessible description.
* Logical focus order.

Screen readers should immediately announce the modal title.

---

# Responsive Behavior

Desktop:

Centered modal.

Tablet:

Centered with reduced margins.

Mobile:

Full-screen modal for complex workflows.

Small confirmation dialogs may remain centered.

---

# Loading State

If the modal performs a background task:

* Disable repeated submission.
* Show loading state on the primary button.
* Preserve layout.

Avoid replacing the entire modal with a spinner.

---

# Validation

Validation errors should appear inline.

Do not dismiss the modal until validation succeeds.

The user should clearly understand what needs to be corrected.

---

# Error State

If an operation fails:

* Explain the issue.
* Preserve entered information.
* Allow retry where appropriate.

Never force users to re-enter data unnecessarily.

---

# Animation

Opening:

* Fade overlay.
* Scale modal from 98% to 100%.

Closing:

* Reverse transition.

Duration:

```text
250ms
```

Animation should support orientation, not decoration.

---

# Anti-Patterns

Do not:

* Stack multiple modals.
* Use modals for navigation.
* Display long forms when a dedicated page is more appropriate.
* Auto-open promotional dialogs.
* Trap users without an obvious exit.

One modal should solve one problem.

---

# Implementation Tokens

```css
--modal-radius: var(--radius-2xl);
--modal-padding: var(--space-6);

--modal-shadow: var(--shadow-xl);

--modal-width-sm: 400px;
--modal-width-md: 600px;
--modal-width-lg: 800px;
```

---

# Definition of Done

A modal implementation is complete when:

* It follows documented layout rules.
* Keyboard focus is managed correctly.
* Accessibility requirements are satisfied.
* Closing behavior matches this specification.
* Loading and validation states are implemented.

---

# Implementation Notes

### Frontend

* Build a reusable `<Modal />` component with composable `Header`, `Body`, and `Footer` sections.
* Manage focus automatically when opening and closing.
* Support configurable sizes using documented tokens.

### Backend

* Not applicable.

### AI Coding Agent

* Never use a modal for routine success messages.
* Prefer inline interactions wherever possible.
* Use confirmation modals only for meaningful, potentially destructive actions.
* Do not stack modals.

---

# Future Considerations

Future versions may introduce:

* Side panels for editing.
* Multi-step modal workflows.
* Split-view comparison dialogs.
* Advanced import wizards.

These should follow the same interaction principles and avoid unnecessary interruption.

---

# Closing

A modal temporarily asks for the user's full attention.

That attention should always be respected.

If users begin closing modals without reading them, the design has failed.

A successful modal appears rarely, communicates clearly, and disappears as soon as its purpose is fulfilled.
