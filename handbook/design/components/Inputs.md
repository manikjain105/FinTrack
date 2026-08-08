---
title: Inputs
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
  - ../foundation/Motion.md
  - ../foundation/Accessibility.md
---

# Inputs

> **Every input should make data entry feel effortless.**

---

# Purpose

This document defines the standard input components used throughout FinTrack.

Inputs collect user information.

They should be predictable, accessible, forgiving, and fast.

The user should always know:

* what to enter,
* why it is required,
* whether it is valid.

---

# Design Philosophy

Typing is one of the most common interactions in FinTrack.

Inputs should disappear into the workflow.

Users should focus on their financial information—not the form itself.

---

# Input Principles

Every input should:

* Be immediately understandable.
* Be accessible.
* Minimize typing.
* Prevent mistakes where possible.
* Provide immediate feedback.
* Support keyboard-first interaction.

---

# Standard Specifications

| Property           |     Value |
| ------------------ | --------: |
| Height             |      44px |
| Border Radius      | radius-md |
| Horizontal Padding |   space-4 |
| Vertical Padding   |   space-3 |
| Typography         |      Body |
| Font Weight        |       400 |

---

# Supported Input Types

Version 1 supports:

* Text
* Number
* Currency
* Email
* Password
* Search
* Multiline (Textarea)

No additional input types should be introduced without documentation.

---

# Input Anatomy

Every input consists of:

```text
Label

↓

Input Field

↓

Supporting Text (optional)

↓

Validation Message (optional)
```

Labels should always appear above the input.

Avoid placeholder-only forms.

---

# Labels

Labels should:

* Clearly describe the expected input.
* Be concise.
* Use sentence case.

Good examples:

* Monthly Budget
* Category Name
* Currency

Avoid:

* Enter Budget
* Type Here
* Input Value

---

# Placeholder Text

Placeholders provide examples.

They do not replace labels.

Examples:

```text
₹50,000

Food

Coffee with friends
```

Placeholder text should use the **Text Muted** semantic token.

---

# Supporting Text

Supporting text explains:

* Expected format.
* Constraints.
* Helpful guidance.

Example:

> Used to calculate monthly spending progress.

Keep supporting text concise.

---

# Validation

Validation should happen as early as practical without interrupting the user.

Use:

* Success state
* Warning state
* Error state

Validation messages should explain:

* What went wrong.
* How to fix it.

Example:

❌ Invalid.

Good:

> Budget must be greater than ₹0.

---

# Required Fields

Required fields should be kept to a minimum.

Avoid unnecessary mandatory inputs.

If a sensible default exists, use it.

---

# Disabled Inputs

Disabled inputs should:

* Remain readable.
* Clearly communicate they cannot be edited.
* Never hide important information.

---

# Read-Only Inputs

Read-only fields:

* Allow text selection.
* Cannot be edited.
* Should look different from disabled inputs.

Examples:

* User ID
* Account Email

---

# Focus State

Focus should include:

* Visible focus ring
* Updated border color
* High contrast

Focus must never rely solely on color.

---

# Error State

Error styling includes:

* Danger border
* Error message
* Optional error icon

The user should never have to guess what needs correction.

---

# Success State

Use success sparingly.

Suitable examples:

* Import completed.
* Budget saved.
* Profile updated.

Do not show green borders simply because a field contains valid data.

---

# Input Icons

Icons may appear:

* Leading
* Trailing

Leading examples:

* Search
* Currency

Trailing examples:

* Show Password
* Clear Input

Icons must never reduce readability.

---

# Keyboard Behavior

Every input must support:

* Tab navigation
* Shift + Tab
* Copy
* Paste
* Undo
* Redo
* Select All

Standard operating system shortcuts should always work.

---

# Mobile Behavior

Use appropriate HTML input types.

Examples:

```html
<input type="email">

<input type="number">

<input inputmode="decimal">
```

This ensures mobile devices display the correct keyboard.

---

# Accessibility

Every input must have:

* Associated label
* Accessible name
* Keyboard navigation
* Error announcement (`aria-describedby`)
* Visible focus state

Placeholder text alone is never sufficient.

---

# Anti-Patterns

Do not:

* Hide labels.
* Use placeholder-only forms.
* Delay validation until submission when immediate validation is appropriate.
* Disable paste.
* Auto-capitalize financial values.
* Force unnecessary formatting while typing.

---

# Implementation Tokens

```css
--input-height: 44px;
--input-radius: var(--radius-md);
--input-padding-x: var(--space-4);
--input-padding-y: var(--space-3);
```

---

# Definition of Done

An input component is complete when:

* It follows the documented dimensions.
* Supports keyboard interaction.
* Meets accessibility requirements.
* Uses design tokens exclusively.
* Provides clear validation feedback.

---

# Implementation Notes

### Frontend

* Create a reusable `<Input />` component.
* Build specialized variants (`SearchInput`, `CurrencyInput`) on top of the base component.
* Keep validation styling centralized.

### Backend

* Treat client-side validation as a convenience.
* Always validate input again on the server.

### AI Coding Agent

* Never create one-off input styles.
* Extend the base Input component instead of duplicating behavior.
* Reuse validation patterns consistently.

---

# Future Considerations

Future versions may introduce:

* Auto-complete inputs.
* Smart merchant suggestions.
* Currency conversion inputs.
* Date pickers.

These should inherit from the base Input specification whenever possible.

---

# Closing

An input is the beginning of a conversation between the user and the application.

That conversation should always feel clear, forgiving, and efficient.
