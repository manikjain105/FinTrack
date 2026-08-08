# Glossary

This glossary defines the shared vocabulary used throughout the FinTrack Handbook.

Consistent terminology keeps the Foundation, Design, Product, and Engineering sections aligned.

When a term is used in documentation, it should match the definition here.

---

# How to Use This Glossary

* Use these terms consistently across all documentation.
* Prefer glossary terms over synonyms.
* If a new concept emerges, define it here before using it widely.
* If two documents disagree, the definition here takes precedence for terminology.

---

# Product Terms

## FinTrack

The personal finance application described by this handbook.

---

## Transaction

A single financial record representing money spent or received.

Every transaction has an amount, type, category, date, and optional merchant and notes.

---

## Income

A transaction that increases available money.

---

## Expense

A transaction that decreases available money.

---

## Category

A label that groups transactions by purpose (for example, Food, Travel, Rent).

---

## Merchant

The party a transaction was paid to or received from (for example, Swiggy, Uber).

---

## Budget

A planned spending limit for a month, optionally scoped to a single category.

---

## Monthly Budget

The overall spending limit for a given month.

---

## Category Budget

A spending limit for one category within a month.

---

## Insight

A data-derived observation that helps the user understand spending or make a decision.

Insights are always based on the user's own data.

---

## Dashboard

The financial home screen that summarizes the current month at a glance.

---

## Command Palette

The primary, keyboard-first input for recording transactions using natural language.

---

## Selected Month

The month currently being viewed. Metrics, charts, and budgets always reflect the selected month.

---

# Design Terms

## Design Token

A named, reusable visual value (color, spacing, radius, shadow, motion duration) consumed by components instead of hardcoded values.

---

## Component

A reusable interface building block (for example, Button, Input, Modal, Card).

---

## Base Card

The foundational card component from which specialized cards inherit.

---

## Summary Card

A card that displays one key metric at a glance.

---

## Budget Card

A card that displays spending progress against a budget.

---

## Insight Card

A card that presents a data-derived observation.

---

## Application Shell

The persistent interface (sidebar, top bar, content region, toast layer) that surrounds every page.

---

## Empty State

The display shown when no data is available, guiding the user toward a next action.

---

## Loading State

The display shown while data is being retrieved, preserving layout stability.

---

## Semantic Color

A color referenced by meaning (Success, Warning, Danger, Info) rather than by raw value.

---

# Engineering Terms

## Local-First

An architecture in which all data is stored on the user's device and the application functions without a network connection.

---

## Layer

A section of the architecture with a single responsibility (Presentation, API, Business Logic, Persistence).

---

## Service Layer

The layer that contains business logic such as calculations, budget evaluation, and report generation.

---

## Repository

The component that isolates database access from business logic.

---

## Schema

The definition of database tables, columns, relationships, and constraints.

---

## Migration

A versioned, reproducible change to the database schema.

---

## Index

A database structure that accelerates frequently executed queries.

---

## Parser

The component that converts natural-language input into structured transaction data.

---

## Endpoint

A single API route with a defined request and response contract.

---

## Confidence (Parser)

A measure of how certain the parser is about an interpreted transaction, used to decide whether to save automatically or ask the user.

---

# Documentation Terms

## Handbook

The complete set of Foundation, Design, Product, and Engineering documentation.

---

## Source of Truth

The single authoritative location for a given piece of information.

---

## Acceptance Criteria

The measurable conditions that define when a feature or specification is complete.

---

## Definition of Done

The checklist a piece of work must satisfy before it is considered finished.

---

# Contributing

When adding a new term:

* Place it under the correct section.
* Keep the definition concise.
* Avoid duplicating definitions across documents.
* Reference the term consistently everywhere else.

---

# Goal

The glossary should give everyone—developers, designers, and AI coding agents—a shared, unambiguous vocabulary for discussing and building FinTrack.
