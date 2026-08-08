---
title: Navigation
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - Application-Shell.md
  - ../foundation/Colors.md
  - ../foundation/Typography.md
  - ../foundation/Spacing.md
  - ../foundation/Motion.md
  - ../foundation/Icons.md
---

# Navigation

> **Navigation should answer one question: "Where can I go next?"**

---

# Purpose

This document defines the navigation system used throughout FinTrack.

Navigation provides a consistent way for users to move between the application's primary areas.

Navigation should remain predictable across all pages and devices.

---

# Design Philosophy

Navigation should disappear into muscle memory.

Users should never need to think about where a destination is located.

Primary navigation should remain stable throughout the lifetime of the application.

Avoid frequently changing the structure or order of navigation items.

---

# Navigation Principles

The navigation system should:

* Be consistent.
* Be easy to scan.
* Clearly indicate the current location.
* Require minimal interaction.
* Support keyboard navigation.
* Adapt gracefully to different screen sizes.

---

# Primary Navigation

Version 1 contains the following destinations:

| Order | Destination  |
| ----: | ------------ |
|     1 | Dashboard    |
|     2 | Transactions |
|     3 | Budgets      |
|     4 | Analytics    |
|     5 | Settings     |

This order should remain consistent across desktop and mobile.

---

# Desktop Navigation

Desktop navigation is displayed in the persistent Sidebar.

Each navigation item contains:

* Icon
* Label

Example:

```text
🏠 Dashboard

🧾 Transactions

💰 Budgets

📊 Analytics

⚙ Settings
```

Labels are mandatory.

Icons alone are not sufficient.

---

# Mobile Navigation

Mobile uses a Bottom Navigation Bar.

Maximum items:

```text
5
```

Each item contains:

* Icon
* Short label

The Bottom Navigation should remain fixed while scrolling.

---

# Active State

Exactly one primary destination may be active.

The active item should communicate state using:

* Primary color
* Subtle background
* Increased font weight

The active state must remain visible in both light and dark themes.

---

# Hover State

Desktop only.

Hover may change:

* Background
* Text color
* Border radius

Hover should not change layout.

---

# Focus State

Keyboard focus should include:

* Visible focus ring
* High contrast
* Logical tab order

Focus must never rely solely on color.

---

# Navigation Groups

Version 1 uses a single navigation group.

Future versions may introduce grouped sections.

Example:

```text
Main

Dashboard

Transactions

Budgets

Analytics

General

Settings
```

Groups should remain visually subtle.

---

# Badges

Navigation badges are reserved for important information.

Examples:

* Failed Sync
* Import Running

Avoid permanent numeric badges.

Navigation should not become a notification center.

---

# Collapsed Sidebar

Desktop supports a collapsed navigation state.

Collapsed width:

```text
72px
```

Behavior:

* Icons remain visible.
* Labels are hidden.
* Hover reveals tooltip.

The collapsed state must remain fully usable.

---

# Tooltips

Tooltips are shown only when:

* Sidebar is collapsed.
* An icon-only control requires clarification.

Tooltips should never replace visible labels in the expanded navigation.

---

# Keyboard Shortcuts

Recommended shortcuts:

| Shortcut | Action       |
| -------- | ------------ |
| G D      | Dashboard    |
| G T      | Transactions |
| G B      | Budgets      |
| G A      | Analytics    |
| G S      | Settings     |

These shortcuts are optional for Version 1 but the architecture should support them.

---

# Breadcrumbs

Version 1 does not require breadcrumbs.

The application hierarchy is intentionally shallow.

If future features introduce deeper navigation, breadcrumbs may be added.

---

# Navigation Persistence

Navigation should preserve:

* Scroll position within pages.
* Sidebar collapsed state.
* Selected theme.

Users should return to the same context whenever possible.

---

# Accessibility

Navigation must support:

* Keyboard navigation.
* Screen readers.
* Landmark roles.
* Visible focus.
* Accessible names for icons.

Use:

```html
<nav aria-label="Primary Navigation">
```

The active destination should expose:

```html
aria-current="page"
```

---

# Responsive Behavior

Desktop:

Persistent Sidebar.

Tablet:

Collapsible Sidebar.

Mobile:

Bottom Navigation.

Navigation patterns should remain familiar across devices.

---

# Anti-Patterns

Do not:

* Reorder navigation items dynamically.
* Hide primary destinations behind menus.
* Use icon-only navigation on desktop.
* Display more than one active destination.
* Place page-specific actions inside navigation.

Navigation exists for movement, not actions.

---

# Implementation Tokens

```css
--sidebar-width: 280px;
--sidebar-width-collapsed: 72px;

--nav-item-height: 44px;
--nav-item-gap: var(--space-3);
--nav-item-radius: var(--radius-lg);
```

---

# Definition of Done

Navigation is complete when:

* Primary destinations are consistent.
* Exactly one destination is active.
* Keyboard navigation works correctly.
* Desktop and mobile behaviors match this specification.
* Accessibility requirements are satisfied.

---

# Implementation Notes

### Frontend

* Build reusable `<Sidebar />` and `<BottomNavigation />` components.
* Define navigation items from a shared configuration object rather than hardcoding them.
* Keep navigation state separate from page content.

### Backend

* Not applicable.

### AI Coding Agent

* Do not hardcode navigation items in multiple places.
* Use a single source of truth for navigation configuration.
* Maintain the documented order of primary destinations.

---

# Future Considerations

Future versions may introduce:

* Workspaces.
* Nested navigation.
* Favorites.
* Recently visited pages.
* Context-aware shortcuts.

These features should extend the existing navigation model rather than replace it.

---

# Closing

Good navigation is rarely noticed.

Users should instinctively know where they are, where they can go, and how to get there.

That familiarity builds confidence, and confidence builds daily habits.
