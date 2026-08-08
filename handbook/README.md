# FinTrack Handbook

Welcome to the **FinTrack Handbook**.

This handbook is the single source of truth for the product, design decisions, and implementation philosophy behind FinTrack.

It is intended for:

* Developers
* Designers
* AI Coding Agents
* Future contributors

The handbook explains **why** FinTrack is built the way it is. It is not intended to contain implementation code or technical specifications.

---

# Reading Order

New contributors should read the handbook in the following order:

1. Foundation
2. Design System
3. Product Documentation
4. Engineering Documentation
5. Architecture Decisions

Following this order provides the necessary context before implementation begins.

---

# Handbook Structure

```text
handbook/

foundation/
    Product vision and philosophy

design/
    Design system and reusable UI components

product/
    Product features and screen specifications

parser/
    Natural language parser documentation

engineering/
    Technical architecture and implementation guidance

decisions/
    Architecture Decision Records (ADRs)
```

---

# Principles

The handbook follows these principles:

* One topic per document.
* Reusable knowledge over duplicated content.
* Components inherit behavior from base specifications.
* Product documentation describes **what** to build.
* Engineering documentation describes **how** to build it.

---

# Source of Truth

When documentation conflicts:

1. Foundation
2. Design
3. Product
4. Engineering

Higher-level documents always take precedence.

---

# Contributing

Before adding new documentation:

* Reuse existing concepts whenever possible.
* Update related documents if behavior changes.
* Keep naming consistent.
* Avoid duplicating specifications.

Every significant design or architectural decision should be documented before implementation.

---

# Goal

The handbook exists so that any developer—or AI coding agent—can understand FinTrack, implement features consistently, and maintain the product over time.
