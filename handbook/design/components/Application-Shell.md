---
title: Application Shell
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - ../foundation/Grid.md
  - ../foundation/Spacing.md
  - ../foundation/Typography.md
  - ../foundation/Colors.md
  - ../foundation/Motion.md
  - ../foundation/Borders-and-Radius.md
---

# Application Shell

> **The Application Shell provides the persistent structure of FinTrack.**

---

# Purpose

The Application Shell defines the persistent interface that surrounds every page in FinTrack.

The shell is responsible for:

* Navigation
* Global actions
* Layout consistency
* Responsive behavior
* Page transitions

Only the page content changes.

The shell remains consistent.

---

# Design Philosophy

The shell should disappear into the background.

Users should immediately know:

* where they are,
* how to navigate,
* and where to perform common actions.

The shell supports the product.

It should never become the product.

---

# Desktop Layout

```text
┌─────────────────────────────────────────────────────────────────────┐
│ Sidebar │ Top Bar                                                   │
│         ├───────────────────────────────────────────────────────────┤
│         │                                                           │
│         │                                                           │
│         │                 Page Content                              │
│         │                                                           │
│         │                                                           │
│         │                                                           │
└─────────────────────────────────────────────────────────────────────┘
```

---

# Shell Regions

The application consists of four persistent regions.

1. Sidebar
2. Top Bar
3. Main Content
4. Toast Layer

Each region has a single responsibility.

---

# Sidebar

Purpose:

Primary navigation.

Contains:

* Logo
* Dashboard
* Transactions
* Analytics
* Budgets
* Settings

Optional future items:

* Investments
* Goals
* Reports

Sidebar width:

```text
280px
```

Collapsed:

```text
72px
```

---

# Top Bar

Purpose:

Global actions.

Contains:

* Page title
* Search (future)
* Theme toggle
* User menu
* Sync status
* Notifications (future)

The Top Bar never contains page-specific actions.

---

# Main Content

Contains:

Only page-specific content.

The shell should not influence feature layouts beyond spacing and container constraints.

---

# Toast Layer

Toasts appear above all content.

Location:

Bottom-right (desktop).

Bottom-center (mobile).

Maximum:

Three simultaneous toasts.

---

# Content Width

Maximum content width:

```text
1440px
```

Centered within the available viewport.

---

# Page Padding

Desktop:

```text
space-7
```

Tablet:

```text
space-6
```

Mobile:

```text
space-4
```

---

# Page Title

Every page begins with:

* Title
* Optional description

Example:

```
Dashboard

Your financial overview for July.
```

The title belongs to the page—not the Top Bar.

---

# Scrolling

Only the Main Content region scrolls.

The Sidebar and Top Bar remain fixed.

This preserves orientation and improves navigation.

---

# Navigation State

Exactly one primary navigation item may be active.

The active state should be clearly distinguishable using:

* Primary color
* Background
* Font weight

Avoid relying on color alone.

---

# Responsive Behavior

Desktop:

Persistent sidebar.

Tablet:

Collapsible sidebar.

Mobile:

Bottom navigation.

The shell should adapt without changing the user's mental model.

---

# Keyboard Support

The shell must support:

* Tab navigation.
* Skip to content.
* Keyboard focus.
* Global shortcuts.

The shell should never trap keyboard focus.

---

# Accessibility

Provide:

* Landmark roles.
* Navigation regions.
* Main content region.
* Skip links.

Screen readers should easily distinguish shell elements from page content.

---

# Anti-Patterns

Do not:

* Place page-specific buttons inside the shell.
* Allow multiple active navigation items.
* Scroll the sidebar independently.
* Duplicate navigation inside pages.

The shell exists to simplify navigation—not compete with page content.

---

# Implementation Notes

### Frontend

* Build a reusable `<AppShell />` component.
* Accept page content through composition (`children`).
* Keep shell state independent of page state.

### Backend

* Not applicable.

### AI Coding Agent

* Every page must render inside `<AppShell />`.
* Never duplicate navigation outside the shell.
* Keep shell behavior consistent across routes.

---

# Future Considerations

Future versions may introduce:

* Multi-workspace support.
* Global command search.
* Background sync indicators.
* Notification center.
* Multiple accounts.

These features should extend the shell without changing its fundamental structure.

---

# Definition of Done

The Application Shell is complete when:

* Navigation is persistent.
* The Top Bar remains consistent.
* Only the content region changes between pages.
* Responsive behavior matches this specification.
* Accessibility requirements are satisfied.

---

# Closing

The Application Shell is the foundation every screen rests upon.

When implemented correctly, users stop noticing it entirely.

They simply feel that every page belongs to the same product.
