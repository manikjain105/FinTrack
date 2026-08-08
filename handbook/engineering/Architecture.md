---
title: Architecture
category: Engineering
status: Approved
version: 1.0
owner: Engineering
depends_on:
  - Engineering Principles
  - Technology Stack
  - Product Blueprint
related:
  - Project Structure
  - Database
  - Parser
  - API Design
---

# Architecture

> **The architecture should make the correct implementation the easiest implementation.**

---

# Purpose

This document defines the high-level architecture of FinTrack.

It explains how the application's major systems interact, where responsibilities belong, and how data flows through the product.

The architecture should prioritize:

* Simplicity
* Maintainability
* Reliability
* Privacy
* Scalability

---

# Architectural Philosophy

FinTrack follows a **layered, local-first architecture**.

Each layer has a single responsibility.

Higher layers depend on lower layers.

Lower layers never depend on higher layers.

This keeps the application modular and easy to evolve.

---

# High-Level Architecture

```text
┌─────────────────────────────┐
│        React Frontend       │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│        FastAPI Backend      │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│     Business Logic Layer    │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│      SQLite Database        │
└─────────────────────────────┘
```

Each layer communicates only with its immediate neighbor.

---

# Architectural Layers

## Presentation Layer

Responsible for:

* Rendering UI.
* Handling user interactions.
* Displaying data.
* Client-side validation.

The Presentation Layer should contain no business rules.

---

## API Layer

Responsible for:

* Receiving requests.
* Validating input.
* Returning structured responses.
* Error handling.

The API Layer should remain thin.

Business logic belongs elsewhere.

---

## Business Logic Layer

Responsible for:

* Financial calculations.
* Budget evaluation.
* Parser orchestration.
* Report generation.
* Analytics calculations.

This layer represents the application's core intelligence.

---

## Persistence Layer

Responsible for:

* Reading data.
* Writing data.
* Database transactions.
* Query optimization.

Persistence should never contain business rules.

---

# Dependency Direction

Dependencies should always flow downward.

```text
Frontend

↓

API

↓

Business Logic

↓

Database
```

Reverse dependencies should never exist.

---

# Module Responsibilities

Each module should own one responsibility.

Examples:

```text
Parser

↓

Converts natural language
into structured transactions.
```

```text
Analytics

↓

Produces financial insights.
```

```text
Database

↓

Stores financial records.
```

No module should perform unrelated tasks.

---

# Data Flow

Adding a transaction follows this sequence:

```text
User

↓

Frontend

↓

API

↓

Parser

↓

Business Logic

↓

Database

↓

Business Logic

↓

Frontend
```

Every request should have a predictable lifecycle.

---

# Business Rule Ownership

Business rules belong exclusively to the Business Logic Layer.

Examples:

* Budget calculations.
* Spending projections.
* Category assignment.
* Financial summaries.

Neither the Frontend nor Database should duplicate these rules.

---

# Error Flow

Errors should move upward.

```text
Database Error

↓

Business Logic

↓

API

↓

Frontend

↓

User-friendly Message
```

Internal implementation details should never be exposed directly to users.

---

# Configuration

Application configuration should remain centralized.

Examples:

* Currency
* Theme
* Budget defaults
* Categories
* File locations

Configuration should never be hardcoded across multiple modules.

---

# Extensibility

The architecture should support future additions such as:

* Cloud synchronization.
* User accounts.
* Mobile clients.
* AI categorization.
* Background jobs.

New features should extend existing layers rather than bypass them.

---

# Architectural Constraints

Version 1 intentionally excludes:

* Microservices.
* Distributed databases.
* Event buses.
* Message queues.
* Background workers.
* Complex caching systems.

These technologies introduce unnecessary complexity for the current scope.

---

# Performance Considerations

The architecture should:

* Minimize unnecessary database queries.
* Avoid duplicate calculations.
* Keep API requests lightweight.
* Cache only when measurement justifies it.

Optimize based on evidence, not assumptions.

---

# Security Considerations

The architecture should:

* Validate every external input.
* Sanitize uploaded files.
* Restrict database access to the Persistence Layer.
* Avoid exposing internal implementation details.

Security applies across every architectural layer.

---

# Testing Strategy

Each layer should be independently testable.

Examples:

* Parser tests.
* Business logic tests.
* Database tests.
* API tests.
* Frontend component tests.

Layer isolation improves reliability.

---

# AI Coding Agent Guidance

When implementing features:

* Respect the documented layer boundaries.
* Do not bypass the Business Logic Layer.
* Do not place business rules in UI components.
* Reuse existing modules whenever possible.

Architecture should remain consistent even as the application grows.

---

# Acceptance Criteria

The architecture is correctly implemented when:

* Every layer has a single responsibility.
* Dependency direction is maintained.
* Business rules remain centralized.
* Modules are independently testable.
* Future features can be added without restructuring existing layers.

---

# Future Considerations

Future versions may introduce:

* Offline synchronization.
* Plugin architecture.
* Cloud APIs.
* Background processing.
* Multi-device support.

These additions should extend—not replace—the layered architecture defined here.

---

# Goal

The architecture should make FinTrack easy to understand, easy to maintain, and easy to extend.

A new developer—or AI coding agent—should be able to determine where any new feature belongs simply by following the architectural boundaries described in this document.
