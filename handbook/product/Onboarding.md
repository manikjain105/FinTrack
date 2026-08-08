---
title: Onboarding
category: Product
status: Approved
version: 1.0
owner: Product
depends_on:
  - Dashboard
  - Command Palette
  - Navigation Map
related:
  - Settings
  - Transactions
---

# Onboarding

> **The goal of onboarding is not to explain FinTrack. It is to help users record their first transaction successfully.**

---

# Purpose

The Onboarding experience introduces new users to FinTrack by guiding them through the minimum number of steps required to begin tracking expenses.

Onboarding should feel lightweight, welcoming, and optional.

Users should reach their first successful transaction in under two minutes.

---

# Design Philosophy

FinTrack follows a **progressive disclosure** approach.

Users learn features naturally as they begin using the application.

Avoid long tutorials, feature tours, or mandatory walkthroughs.

---

# User Goals

New users should be able to:

* Understand what FinTrack does.
* Record their first transaction.
* Set an initial monthly budget (optional).
* Recognize where to find future features.

---

# First Launch Experience

On first launch, users are greeted with:

```text
Welcome to FinTrack

Track your spending.
Understand your habits.
Stay within your budget.

[Get Started]
```

The message should remain concise and action-oriented.

---

# Onboarding Flow

```text
Welcome

↓

Choose Currency

↓

Set Monthly Budget (Optional)

↓

Record First Transaction

↓

Dashboard
```

Users may skip optional steps.

---

# Step 1 — Welcome

Explain:

* What FinTrack does.
* That all data is stored locally (Version 1).
* That users retain ownership of their data.

Do not overwhelm users with feature lists.

---

# Step 2 — Choose Currency

Version 1 defaults to:

```text
₹ Indian Rupee
```

Users may change this later in Settings.

---

# Step 3 — Monthly Budget (Optional)

Offer users the option to define a monthly spending goal.

If skipped:

The Dashboard should continue working normally.

---

# Step 4 — First Transaction

Guide users to enter an example transaction.

Suggested placeholder:

```text
coffee 180
```

After successful submission:

* Display a confirmation toast.
* Update the Dashboard immediately.
* Reveal Summary Cards and Insights.

This is the primary success moment.

---

# Completion

After the first transaction:

Display:

```text
You're all set!

Your dashboard will grow smarter as you add more transactions.
```

Users are taken directly to the Dashboard.

---

# Skipping Onboarding

Users may skip onboarding entirely.

If skipped:

* Default preferences are applied.
* Dashboard opens immediately.
* Onboarding is not shown again unless reset.

---

# Returning Users

Onboarding is shown only once.

Future launches open directly to the Dashboard.

A reset option may be added in future versions.

---

# Empty Dashboard Experience

If users skip adding a transaction:

Display:

* Empty Summary Cards.
* Empty Budget Card.
* Helpful examples.
* Command Palette.

The Dashboard should still feel complete.

---

# User Flows

## Standard Flow

```text
Welcome

↓

Currency

↓

Budget

↓

First Transaction

↓

Dashboard
```

---

## Skip Flow

```text
Welcome

↓

Skip

↓

Dashboard
```

---

# Business Rules

* Onboarding appears only for first-time users.
* Currency selection updates application formatting.
* Budget creation is optional.
* Completing onboarding requires only one successful transaction.
* Preferences are stored locally.

---

# Loading State

Loading should be minimal.

If required:

Display lightweight placeholders while initializing the application.

---

# Error State

If onboarding data cannot be saved:

Display:

```text
Unable to complete setup.

Please try again.
```

Preserve user-entered information whenever possible.

---

# Accessibility

Onboarding must:

* Support keyboard navigation.
* Use semantic headings.
* Provide clear focus indicators.
* Offer sufficient color contrast.
* Allow every step to be completed without a mouse.

---

# Performance Expectations

Onboarding should:

* Launch instantly.
* Complete in under two minutes.
* Never block access to the application.

---

# Acceptance Criteria

The Onboarding experience is complete when:

* New users see the welcome screen.
* Currency can be selected.
* Budget setup is optional.
* Users can record their first transaction.
* Dashboard opens immediately after completion.
* Skipping onboarding works correctly.
* Accessibility requirements are satisfied.

---

# Future Enhancements

Future versions may introduce:

* Interactive product tours.
* Sample demo data.
* Personalized setup recommendations.
* AI-powered budgeting suggestions.
* Video walkthroughs.

These enhancements should remain optional and should never delay the user's first successful interaction.

---

# Goal

A successful onboarding experience is one that users barely remember.

Within minutes, users should stop thinking about learning FinTrack and start using it to manage their finances.

The first transaction is the true beginning of the product experience.
