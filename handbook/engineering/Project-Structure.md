---
title: Project Structure
category: Engineering
status: Approved
version: 1.0
owner: Engineering
depends_on:
  - Architecture
  - Technology Stack
  - Engineering Principles
related:
  - Database
  - Parser
  - API Design
  - State Management
---

# Project Structure

> **A well-organized project makes the correct place for new code obvious.**

---

# Purpose

This document defines the directory structure of FinTrack and the responsibility of every major folder.

The project structure should:

* Be predictable.
* Scale as the application grows.
* Separate concerns clearly.
* Reduce duplication.
* Make navigation easy for both developers and AI coding agents.

---

# Design Philosophy

The folder structure mirrors the application's architecture.

Each folder owns a single responsibility.

Code should be organized by **feature and responsibility**, not by convenience.

---

# Repository Structure

```text
FinTrack/
│
├── handbook/
├── frontend/
├── backend/
├── database/
├── scripts/
├── tests/
├── assets/
├── docs/
├── .github/
├── .gitignore
├── README.md
└── LICENSE
```

---

# Top-Level Directories

| Directory | Responsibility                                 |
| --------- | ---------------------------------------------- |
| handbook  | Product, design, and engineering documentation |
| frontend  | React application                              |
| backend   | FastAPI application                            |
| database  | SQLite database and migrations                 |
| scripts   | Utility and automation scripts                 |
| tests     | Automated tests                                |
| assets    | Images, icons, fonts, sample files             |
| docs      | Public documentation and generated docs        |
| .github   | GitHub workflows and templates                 |

Each top-level directory should have a clearly defined purpose.

---

# Frontend Structure

```text
frontend/
│
├── public/
├── src/
│   ├── app/
│   ├── components/
│   ├── features/
│   ├── hooks/
│   ├── layouts/
│   ├── pages/
│   ├── services/
│   ├── store/
│   ├── styles/
│   ├── types/
│   ├── utils/
│   └── main.tsx
│
├── package.json
└── vite.config.ts
```

---

# Frontend Responsibilities

## app/

Application bootstrap.

## components/

Reusable UI components defined by the Design System.

Examples:

* Button
* Input
* Modal
* Table

Components should remain generic.

---

## features/

Feature-specific UI.

Examples:

* Dashboard
* Transactions
* Budgets
* Analytics

Feature code belongs here rather than inside `components`.

---

## hooks/

Reusable custom React hooks.

Examples:

* useTransactions
* useBudget
* useAnalytics

---

## layouts/

Application layout components.

Examples:

* Application Shell
* Sidebar
* Header

---

## pages/

Route-level screens.

Pages compose features and layouts.

---

## services/

Frontend communication layer.

Responsibilities:

* API requests
* File downloads
* Data transformation

No business logic belongs here.

---

## store/

Application state.

Examples:

* Current month
* Theme
* User preferences

Business calculations should remain in the backend.

---

## styles/

Global styles.

Design tokens should remain centralized.

---

## types/

Shared TypeScript interfaces.

---

## utils/

Pure helper functions.

Avoid business-specific calculations here.

---

# Backend Structure

```text
backend/
│
├── api/
├── core/
├── database/
├── models/
├── parsers/
├── repositories/
├── schemas/
├── services/
├── utils/
├── main.py
└── requirements.txt
```

---

# Backend Responsibilities

## api/

HTTP endpoints.

Should remain thin.

---

## core/

Application configuration.

Examples:

* Settings
* Logging
* Constants

---

## database/

Database connection and session management.

---

## models/

SQLAlchemy models.

Only persistence models belong here.

---

## parsers/

Natural-language parser.

Examples:

* Amount parsing
* Category detection
* Merchant extraction

---

## repositories/

Database access.

Repositories isolate SQL from business logic.

---

## schemas/

Pydantic request and response models.

---

## services/

Business logic.

Examples:

* Budget calculations
* Report generation
* Analytics
* Transaction management

This is the heart of the backend.

---

## utils/

Generic helper utilities.

Avoid placing business rules here.

---

# Database Directory

```text
database/
│
├── fintrack.db
├── migrations/
└── seeds/
```

---

# Scripts Directory

Utility scripts only.

Examples:

* Import sample data
* Generate reports
* Backup database
* Reset development environment

Scripts should never contain production business logic.

---

# Tests Structure

```text
tests/
│
├── frontend/
├── backend/
├── integration/
└── fixtures/
```

Tests should mirror the production structure wherever possible.

---

# Assets Structure

```text
assets/
│
├── icons/
├── illustrations/
├── fonts/
└── sample-data/
```

Assets should remain organized by type.

---

# Naming Conventions

Directories:

```text
lowercase
```

Examples:

```text
components
services
database
```

Files:

```text
PascalCase.tsx

camelCase.ts

kebab-case.md
```

Examples:

```text
Button.tsx

BudgetCard.tsx

useTransactions.ts

project-structure.md
```

Use one naming convention consistently.

---

# Import Rules

Dependencies should flow inward.

```text
Pages

↓

Features

↓

Components

↓

Utilities
```

Lower-level modules should never depend on higher-level modules.

---

# Ownership

Every folder should have one clearly defined responsibility.

If a file seems to belong in multiple places, reconsider the architecture.

Ambiguous ownership often indicates an architectural problem.

---

# AI Coding Agent Guidance

When creating new files:

* Prefer extending existing folders.
* Avoid creating new top-level directories.
* Place code according to responsibility, not feature popularity.
* Reuse shared components before creating new ones.

Every new module should have an obvious home.

---

# Acceptance Criteria

The project structure is complete when:

* Every major responsibility has a dedicated folder.
* Folder purposes are clearly documented.
* Architecture and folder structure remain aligned.
* New contributors can locate code quickly.
* AI coding agents can determine where new code belongs without guesswork.

---

# Future Considerations

Future versions may introduce:

* Mobile application.
* Desktop application.
* Shared packages.
* Plugin architecture.
* Cloud services.

These additions should extend the existing structure rather than replacing it.

---

# Goal

The project structure should make FinTrack easy to navigate from day one.

Developers should spend their time building features—not searching for where code belongs.

A clean structure is an investment in every future contribution.
