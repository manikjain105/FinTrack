---
title: Product Blueprint
version: 1.0
status: Approved
owner: Product
references:
  - Manifesto.md
  - Vision.md
---

# FinTrack Product Blueprint

> **Version 1 is not about tracking more.**
>
> **It is about making tracking effortless.**

---

# Purpose

This document defines the complete product experience for FinTrack Version 1.

Unlike the Manifesto, which explains our beliefs, and the Vision, which describes our long-term direction, this blueprint defines exactly what users should experience every time they open the application.

If there is uncertainty during design or implementation, this document takes precedence over assumptions.

---

# Product Summary

FinTrack is a command-first personal finance application.

Users should be able to:

* Record expenses in seconds.
* Understand where money is going.
* Stay within budget.
* Search financial history instantly.
* Access the same data across every device.

Nothing in Version 1 should distract from these goals.

---

# Product Pillars

Every feature must support at least one of these pillars.

## Pillar 1 — Capture

Recording money should be effortless.

The application should reduce typing, eliminate repetitive decisions, and remember previous behavior wherever possible.

---

## Pillar 2 — Understand

Users should immediately understand:

* what changed,
* where money went,
* whether they're on track.

Charts exist to answer questions, not decorate the interface.

---

## Pillar 3 — Improve

The application should encourage better decisions through clarity.

It should never shame users.

It should reveal patterns.

---

## Pillar 4 — Trust

Users should always trust:

* their data,
* calculations,
* synchronization,
* privacy.

Trust is earned through consistency.

---

# Core User Journey

The ideal daily experience is intentionally short.

```text
Open FinTrack

↓

Cursor already focused on Command Palette

↓

Type

coffee 180

↓

Press Enter

↓

Saved

↓

Dashboard updates

↓

Close App
```

Target time:

**Less than three seconds.**

If a workflow takes longer, it should be redesigned.

---

# Primary Navigation

Version 1 intentionally has very little navigation.

```
Dashboard

Transactions

Settings
```

That's all.

Everything else should happen inside these three areas.

---

# Dashboard

The dashboard is the application's home.

It should answer the following questions without scrolling:

* How much have I spent this month?
* How much income have I received?
* How much budget remains?
* Where is my money going?
* Am I doing better than last month?

If the user has to search for these answers, the dashboard has failed.

---

# Command Palette

The command palette is the heart of FinTrack.

It should always be visible near the top of the dashboard.

Examples:

```text
coffee 180

swiggy 420 dinner

rent 18000

salary 85000

uber 260 airport
```

The command palette should feel closer to chatting than filling out a form.

---

# Smart Parsing

The parser should infer as much information as possible.

Typing:

```text
swiggy 420
```

Should automatically determine:

Merchant → Swiggy

Category → Food

Amount → ₹420

Date → Today

Transaction Type → Expense

The user should only correct information when the application is uncertain.

---

# Dashboard Layout

Version 1 consists of nine sections.

## 1. Hero Summary

Displays:

* Monthly Spend
* Monthly Income
* Remaining Budget
* Savings

---

## 2. Command Palette

Primary input.

Always visible.

---

## 3. Budget Overview

Progress bar.

Remaining amount.

Projected month-end spending.

---

## 4. Spending Breakdown

Interactive donut chart.

Category percentages.

---

## 5. Daily Spending Trend

Line chart showing cumulative spending.

Ideal budget pace overlay.

---

## 6. Monthly Comparison

Last six months.

Income vs Expense.

---

## 7. Recent Transactions

Latest activity.

Inline editing.

Delete.

Undo.

---

## 8. Insights

Automatically generated observations.

Examples:

* Largest spending category.
* Highest expense.
* Categories exceeding budget.
* Average daily spend.
* Month-over-month change.

---

## 9. Search

Instant filtering across all transactions.

Search should feel like searching email.

---

# Transactions

Every transaction should include:

* Amount
* Merchant
* Category
* Note
* Date
* Transaction Type

Actions:

* Edit
* Delete
* Duplicate
* Undo

Editing should happen inline.

Avoid modal dialogs unless absolutely necessary.

---

# Search

The search experience should be fast enough that users stop manually browsing transactions.

Supported queries include:

```text
food

amazon

>1000

july

salary

coffee
```

Search results should update while typing.

---

# Settings

Settings should be simple.

Version 1 includes:

* Currency
* Monthly Budget
* Category Budgets
* Categories
* Merchant Mappings
* Theme
* Export Data
* Import Data

Settings should not feel like a configuration panel.

They should feel approachable.

---

# Authentication

Authentication exists for one purpose:

Synchronize personal data across devices.

Supported methods:

* Google
* Apple
* Email

The user should sign in once and rarely think about authentication again.

---

# Mobile Experience

Version 1 is designed as a Progressive Web App.

Requirements:

* Responsive layout.
* Thumb-friendly controls.
* Installable.
* Fast loading.
* Works well on modern mobile browsers.

The mobile experience should not feel like a desktop page squeezed onto a phone.

---

# What We Deliberately Exclude

The following are **not** part of Version 1:

* Investment portfolio
* Net worth tracking
* Credit cards
* Loans
* EMIs
* Receipt OCR
* Voice input
* AI chat
* Tax planning
* Shared accounts
* Notifications

These ideas are valuable.

They simply do not support the Version 1 mission.

---

# Definition of Version 1

Version 1 is complete when a user can:

* Sign in.
* Add a transaction in under three seconds.
* Edit mistakes easily.
* Search history instantly.
* Understand spending immediately.
* Stay within budget.
* Open the application on another device and continue exactly where they left off.

Nothing more is required.

Nothing less is acceptable.

---

# Product Success Metrics

Version 1 will be considered successful if:

* Transaction entry takes less than three seconds.
* Dashboard loads in under one second on a typical connection.
* Search feels instantaneous.
* Users can understand their monthly financial position without navigating away from the dashboard.
* The application remains visually consistent across desktop and mobile.

---

# Closing

The purpose of Version 1 is not to impress users with features.

It is to earn a permanent place in their daily routine.

Every design decision should reduce friction.

Every engineering decision should preserve simplicity.

Every release should strengthen trust.

If users stop thinking about the act of tracking and simply use FinTrack naturally, Version 1 has achieved its purpose.
