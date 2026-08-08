# Design System

The FinTrack Design System defines the visual language, interaction patterns, and reusable interface components used throughout the application.

Its purpose is to ensure that every screen feels consistent, predictable, and cohesive, regardless of who implements it.

The design system is the visual source of truth for FinTrack.

---

# Goals

The Design System exists to:

* Create a consistent user experience.
* Reduce duplicated design decisions.
* Improve implementation quality.
* Increase development speed.
* Make the product easier to maintain.
* Enable AI coding agents to build interfaces with minimal ambiguity.

---

# Design Philosophy

The interface should feel:

* Calm
* Modern
* Professional
* Fast
* Predictable

Every design decision should reduce cognitive load rather than increase it.

Users should spend their attention managing their finances—not learning the interface.

---

# Design Principles

The Design System follows a small number of core principles.

## Consistency

The same interaction should always behave the same way.

---

## Simplicity

Interfaces should remove unnecessary choices.

---

## Accessibility

Every feature should be usable with:

* Keyboard
* Screen reader
* Touch
* Mouse

Accessibility is a default requirement—not an enhancement.

---

## Reusability

Design decisions should be defined once and reused everywhere.

---

## Composition

Large interfaces should be assembled from smaller reusable components rather than built independently.

---

# Reading Order

Read the Design System in the following order.

## Part I — Foundation

```text
Design-Principles

↓

Colors

↓

Typography

↓

Spacing

↓

Grid

↓

Borders-and-Radius

↓

Elevation

↓

Motion

↓

Icons
```

These documents define the visual language.

---

## Part II — Components

```text
Application-Shell

↓

Navigation

↓

Buttons

↓

Inputs

↓

Command-Palette

↓

Progress-Bars

↓

Tables

↓

Toasts

↓

Modals

↓

Empty-States

↓

Loading-States

↓

Cards
```

These documents define reusable UI building blocks.

---

## Part III — Specialized Components

```text
Base-Card

↓

Summary-Card

↓

Budget-Card

↓

Insight-Card
```

These documents define specialized implementations built upon the shared Card component.

---

# Folder Structure

```text
design/

foundation/
    Visual language and design tokens

components/
    Reusable interface components

components/cards/
    Specialized card implementations
```

Each folder has a single responsibility.

---

# Dependency Model

Every layer builds upon the previous one.

```text
Foundation

↓

Components

↓

Specialized Components

↓

Product Screens
```

Product screens should never redefine behavior already documented within the Design System.

---

# Design Tokens

All reusable visual values originate in the Foundation section.

Examples include:

* Colors
* Typography
* Spacing
* Radius
* Borders
* Shadows
* Motion
* Icons

Components should consume these tokens instead of introducing new values.

---

# Component Philosophy

Every component should:

* Solve one problem.
* Have one responsibility.
* Remain reusable.
* Remain accessible.
* Avoid embedding business logic.

Business rules belong in the Product and Engineering documentation.

---

# Relationship to the Product Handbook

The Design System defines **how** interfaces behave.

The Product Handbook defines **what** each screen should do.

Example:

The Design System explains how a Button behaves.

The Product Handbook explains where the "Add Transaction" button appears.

---

# Relationship to Engineering

The Design System does not prescribe implementation details.

It defines behavior, appearance, interaction, and accessibility.

Implementation belongs in the Engineering Handbook.

---

# Contributing

When adding a new component:

1. Check whether an existing component already solves the problem.
2. Extend existing components where appropriate.
3. Reuse design tokens.
4. Update related documentation.
5. Avoid introducing duplicate patterns.

---

# Definition of Done

A new component becomes part of the Design System only when:

* It has a clearly defined purpose.
* It follows the Design Foundation.
* It is reusable.
* It is accessible.
* It includes implementation guidance.
* It does not duplicate an existing component.

---

# Goal

The Design System exists so that every screen in FinTrack feels like it belongs to the same product.

A user should never have to relearn the interface when moving between Dashboard, Transactions, Budgets, Analytics, or Settings.

Consistency is the product's strongest visual feature.
