---
title: Command Palette
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - Inputs.md
  - Buttons.md
  - ../foundation/Typography.md
  - ../foundation/Motion.md
  - ../../foundation/Product-Blueprint.md
---

# Command Palette

> **The fastest way to record a transaction should also be the easiest.**

---

# Purpose

The Command Palette is the primary interaction model of FinTrack.

Users should spend more time thinking about their finances than operating the interface.

The Command Palette exists to remove unnecessary form fields, reduce repetitive input, and make transaction entry feel as natural as typing a message.

It is the default method for creating transactions.

Traditional forms exist only as a fallback.

---

# Product Goal

The Command Palette should allow a user to record a transaction in **under three seconds**.

Every interaction should be optimized toward this goal.

---

# Placement

The Command Palette appears:

* At the top of the Dashboard.
* Immediately below the Hero Summary.
* Above all analytical content.

It is always visible.

It is never hidden behind a menu, modal, or floating action button.

---

# Layout

The component consists of:

```text
┌─────────────────────────────────────────────────────────────┐
│ 💬  Try "coffee 180" or "salary 85000"               [Save] │
└─────────────────────────────────────────────────────────────┘
```

Elements:

* Leading icon.
* Input field.
* Optional inline parser feedback.
* Submit action (desktop only, optional).
* Keyboard shortcut hint (optional).

---

# Placeholder

Rotate between helpful examples.

Examples:

```text
coffee 180

uber 260 airport

rent 18000

salary 85000

swiggy 420 dinner

blinkit 670 groceries
```

Examples should reflect real usage patterns.

---

# Supported Commands

Version 1 supports natural language.

Examples:

```text
coffee 180

swiggy 420 dinner

uber 250

rent 18000

salary 85000

sip 5000

netflix 649

book 799

gym 1500

electricity bill 1850
```

Users should not have to memorize syntax.

Natural language takes priority over commands.

---

# Parsing Behavior

The parser should automatically determine:

* Amount
* Category
* Transaction type
* Date (default: today)
* Merchant (if applicable)
* Note

If confidence is high, save without asking for additional information.

---

# Confidence Rules

| Confidence | Behavior                         |
| ---------- | -------------------------------- |
| 95–100%    | Save immediately                 |
| 80–94%     | Suggest correction before saving |
| Below 80%  | Ask the user for clarification   |

The system should interrupt users only when necessary.

---

# Smart Learning

The Command Palette should remember previous choices.

Examples:

If the user categorizes:

```text
cult.fit
```

as

```text
Health
```

Future entries should automatically use the same category unless overridden.

Merchant learning is local to the user's account.

---

# Auto-Completion

Suggestions should appear while typing.

Examples:

Input:

```text
swi
```

Suggestions:

```text
Swiggy
```

Input:

```text
bla
```

Suggestions:

```text
Blinkit
```

Suggestions should improve speed, not interrupt typing.

---

# Keyboard Shortcuts

| Shortcut     | Action                |
| ------------ | --------------------- |
| Enter        | Save transaction      |
| Esc          | Clear input           |
| ↑ / ↓        | Navigate suggestions  |
| Tab          | Accept suggestion     |
| Ctrl/Cmd + K | Focus Command Palette |

The Command Palette should always support keyboard-first workflows.

---

# Success Flow

Successful entry should feel instantaneous.

Sequence:

1. Parse transaction.
2. Save transaction.
3. Update dashboard.
4. Show success toast.
5. Clear input.
6. Return focus to the Command Palette.

Users should be ready to enter the next transaction immediately.

---

# Error Handling

Errors should be helpful.

Instead of:

> Invalid input.

Use:

> We couldn't understand that transaction.

> Try something like:

```text
coffee 180

uber 260

salary 85000
```

Errors should teach the user rather than block them.

---

# Duplicate Detection

If a nearly identical transaction is entered within a short period:

Example:

```text
coffee 180
```

entered twice within one minute.

Show:

> Similar transaction detected.

Options:

* Save anyway.
* Cancel.

Do not silently reject user input.

---

# Undo

After saving:

Show:

> Saved ₹180 to Food.

**Undo**

Undo remains available for five seconds.

Undo is preferred over confirmation dialogs.

---

# Accessibility

The Command Palette must support:

* Keyboard navigation.
* Screen readers.
* Voice dictation.
* High contrast mode.
* Reduced motion.

Focus should automatically return after every successful save.

---

# Mobile Behavior

The Command Palette remains the primary interaction.

Requirements:

* Large touch target.
* Mobile keyboard optimized.
* No horizontal scrolling.
* Comfortable one-handed use.

The software should adapt to the device without changing the workflow.

---

# Performance

Target response time:

| Action               |     Target |
| -------------------- | ---------: |
| Parse input          |     <50 ms |
| Save transaction     |    <150 ms |
| Dashboard refresh    |    <300 ms |
| Complete interaction | <3 seconds |

The interface should feel immediate.

---

# Analytics

Record anonymous product metrics (never transaction contents):

* Parse success rate.
* Manual correction rate.
* Average entry duration.
* Undo usage.
* Parser confidence distribution.

These metrics help improve the parser over time without compromising user privacy.

---

# Anti-Patterns

Do not:

* Require categories when confidence is high.
* Force users into forms.
* Display multiple confirmation dialogs.
* Interrupt typing with popups.
* Lose keyboard focus after saving.

The fastest workflow should always remain the default workflow.

---

# Implementation Notes

### Frontend

* Build as a dedicated `<CommandPalette />` component.
* Reuse the base `<Input />` component.
* Use debounced parsing for suggestions.
* Preserve cursor position during updates.

### Backend

* Parse commands on the server.
* Store learned merchant mappings per user.
* Return parser confidence with every response.

### AI Coding Agent

* Treat this as the primary feature of FinTrack.
* Optimize for speed over configurability.
* Never replace the Command Palette with traditional forms.
* Maintain keyboard-first behavior throughout.

---

# Future Considerations

Future versions may introduce:

* Voice input.
* OCR receipts.
* AI-assisted parsing.
* Natural-language corrections.
* Multi-transaction commands.

These features should enhance—not replace—the Command Palette.

---

# Definition of Done

The Command Palette is complete when a user can:

* Open the application.
* Type:

```text
coffee 180
```

* Press Enter.
* See the transaction reflected on the dashboard.

...in less than three seconds, without touching the mouse.

---

# Closing

The Command Palette is not a feature.

It is the identity of FinTrack.

If users remember one thing about the product, it should be this experience.

Everything else exists to support it.
