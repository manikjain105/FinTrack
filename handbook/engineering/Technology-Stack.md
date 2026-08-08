---
title: Technology Stack
category: Engineering
status: Approved
version: 1.0
owner: Engineering
depends_on:
  - Product Blueprint
  - Dashboard
  - Transactions
related:
  - Architecture
  - Project Structure
  - Database
---

# Technology Stack

> **Every technology should solve a problem. No technology should exist simply because it is popular.**

---

# Purpose

This document defines the technologies used to build FinTrack and explains why each one was selected.

The objective is to create a product that is:

* Easy to develop
* Easy to understand
* Easy to deploy
* Easy to maintain
* Affordable to operate

Version 1 prioritizes simplicity over scalability.

---

# Engineering Philosophy

FinTrack follows a **local-first** architecture.

Core principles:

* User data belongs to the user.
* Minimize external dependencies.
* Prefer mature, well-documented technologies.
* Avoid unnecessary complexity.
* Build for maintainability first.

---

# Technology Overview

| Layer              | Technology         |
| ------------------ | ------------------ |
| Frontend           | React + TypeScript |
| Styling            | Tailwind CSS       |
| Build Tool         | Vite               |
| Charts             | Recharts           |
| Backend            | Python             |
| API                | FastAPI            |
| Database           | SQLite             |
| ORM                | SQLAlchemy         |
| Validation         | Pydantic           |
| Package Manager    | npm + pip          |
| Version Control    | Git                |
| Hosting (Frontend) | Vercel             |
| Local Backend      | FastAPI Server     |
| Documentation      | Markdown           |

---

# Why React?

React provides:

* Component-based architecture.
* Excellent ecosystem.
* Strong TypeScript support.
* Mature tooling.
* Large developer community.

The Design System naturally maps to reusable React components.

---

# Why TypeScript?

TypeScript improves reliability by providing:

* Static typing.
* Better editor support.
* Safer refactoring.
* Earlier error detection.

Financial applications benefit from stronger type safety.

---

# Why Tailwind CSS?

Tailwind enables:

* Fast UI development.
* Consistent spacing.
* Reusable design tokens.
* Small CSS footprint.

The Design System should define reusable Tailwind utility patterns rather than writing large custom stylesheets.

---

# Why Vite?

Vite provides:

* Extremely fast development startup.
* Fast hot reloading.
* Simple configuration.
* Excellent React support.

It is well suited to small and medium-sized applications.

---

# Why Recharts?

FinTrack requires:

* Line charts
* Bar charts
* Donut charts
* Responsive visualizations

Recharts provides these with minimal complexity and integrates well with React.

---

# Why Python?

Python was selected because:

* Excellent readability.
* Strong ecosystem.
* Mature data-processing libraries.
* Straightforward parser implementation.

It is well suited for financial calculations and natural-language parsing.

---

# Why FastAPI?

FastAPI provides:

* High performance.
* Automatic validation.
* Clear API definitions.
* Excellent developer experience.
* Strong Python integration.

Although Version 1 is primarily local-first, FastAPI establishes a clean architecture that can evolve if future versions introduce synchronization.

---

# Why SQLite?

SQLite provides:

* Zero configuration.
* Single-file database.
* Excellent reliability.
* Fast local performance.
* Easy backup.

For a personal finance application, SQLite is the ideal default database.

---

# Why SQLAlchemy?

SQLAlchemy provides:

* Clean database abstraction.
* Maintainable models.
* Flexible querying.
* Easy migration to larger databases if required in future versions.

---

# Why Pydantic?

Pydantic provides:

* Data validation.
* Clear schemas.
* Type safety.
* Reliable API contracts.

All external input should be validated before processing.

---

# Why Git?

Git provides:

* Version history.
* Safe collaboration.
* Reliable backups.
* Industry-standard workflows.

Every change should be committed with meaningful commit messages.

---

# Why Vercel?

Version 1 hosts only the frontend.

Vercel provides:

* Free hosting for personal projects.
* Automatic deployments.
* HTTPS by default.
* Global CDN.
* Excellent React support.

The backend remains local during Version 1.

---

# Local-First Architecture

Version 1 intentionally separates responsibilities.

```text
Browser (React)

↓

FastAPI (Local)

↓

SQLite
```

Financial data never leaves the user's machine unless the user explicitly exports it.

---

# Version 1 Constraints

Version 1 intentionally excludes:

* Cloud synchronization.
* User accounts.
* Authentication.
* Multi-user collaboration.
* Online databases.

These decisions reduce complexity while preserving privacy.

---

# Upgrade Path

The chosen stack allows future migration to:

* PostgreSQL
* Cloud synchronization
* User authentication
* Mobile applications
* Desktop applications

without requiring a complete rewrite.

---

# Third-Party Dependencies

Only mature and actively maintained libraries should be introduced.

Every dependency should satisfy at least one of these criteria:

* Solves a significant problem.
* Reduces maintenance effort.
* Improves reliability.
* Improves developer productivity.

Avoid dependencies with overlapping responsibilities.

---

# Security Considerations

Technology choices should support:

* Secure local storage.
* Input validation.
* Safe file handling.
* Minimal attack surface.

Sensitive financial data should never be transmitted without explicit user consent.

---

# Performance Considerations

The selected stack should comfortably support:

* 100,000+ transactions.
* Instant search.
* Fast filtering.
* Responsive charts.
* Smooth user interactions.

Performance optimizations should be driven by measurement.

---

# AI Coding Agent Guidance

When implementing features:

* Reuse documented technologies.
* Do not introduce alternative frameworks without documented justification.
* Follow the Design System before creating new UI patterns.
* Prefer existing libraries over custom implementations when they simplify maintenance.

Consistency is more valuable than novelty.

---

# Future Considerations

Future versions may introduce:

* Supabase
* PostgreSQL
* Electron desktop packaging
* Mobile clients
* Background synchronization
* AI-powered categorization

These additions should extend the existing architecture rather than replace it.

---

# Goal

The Technology Stack should provide a stable foundation for FinTrack.

Every chosen technology should contribute to a product that is simple, maintainable, privacy-focused, and enjoyable to build.
