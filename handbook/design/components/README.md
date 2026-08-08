# Components

The Components section defines every reusable user interface component used throughout FinTrack.

Unlike the Design Foundation, which defines visual rules such as colors, typography, spacing, and motion, Components define reusable building blocks that users directly interact with.

Every component should solve exactly one problem.

---

# Reading Order

Read the component specifications in the following order:

1. Application Shell
2. Navigation
3. Buttons
4. Inputs
5. Command Palette
6. Progress Bars
7. Tables
8. Toasts
9. Modals
10. Empty States
11. Loading States
12. Cards

This order reflects the dependency graph between components.

Lower-level components should be understood before higher-level ones.

---

# Component Hierarchy

The FinTrack component library follows a layered architecture.

```text
Design Foundation
        │
        ▼
Application Shell
        │
        ▼
Navigation
        │
        ▼
Buttons ─── Inputs
        │         │
        │         ▼
        │   Command Palette
        │
        ▼
Progress Bars
        │
        ▼
Tables
        │
        ▼
Cards
        │
        ▼
Specialized Cards
```

Every higher-level component builds upon lower-level components whenever possible.

---

# Principles

Every component should:

* Have a single responsibility.
* Be reusable.
* Consume design tokens.
* Be accessible by default.
* Avoid embedding business logic.
* Support keyboard interaction where appropriate.

---

# Component Categories

The component library is divided into four groups.

## Layout Components

Examples:

* Application Shell
* Navigation

These organize the application's structure.

---

## Input Components

Examples:

* Buttons
* Inputs
* Command Palette

These allow users to interact with the application.

---

## Feedback Components

Examples:

* Toasts
* Modals
* Loading States
* Empty States

These communicate application state.

---

## Data Components

Examples:

* Tables
* Progress Bars
* Cards

These present financial information.

---

# Inheritance

Components should extend existing components whenever possible.

Example:

```text
Input

↓

Command Palette
```

```text
Card

↓

Summary Card

↓

Budget Card

↓

Insight Card
```

Inheritance prevents duplication and ensures consistency.

---

# Design Tokens

Components should never define their own:

* Colors
* Typography
* Spacing
* Motion
* Border Radius
* Elevation

All visual values should reference the Design Foundation.

---

# Business Logic

Component documents describe presentation and interaction only.

Business rules belong to:

* Product documentation
* Engineering documentation

Components should remain generic and reusable.

---

# Naming Convention

Component names should be:

* Singular
* Descriptive
* Stable

Examples:

* Button
* Input
* Modal
* Card

Avoid page-specific names.

---

# Source of Truth

If a component specification conflicts with a screen specification:

The component specification takes precedence unless the Product Handbook explicitly documents an approved exception.

---

# Goal

The Components section exists to ensure every part of FinTrack behaves consistently regardless of where it appears.

A reusable component should feel identical whether it is used on the Dashboard, Transactions page, Analytics page, or Settings.
