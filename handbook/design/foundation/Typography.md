---
title: Typography
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - ../README.md
  - Design-Principles.md
  - Colors.md
---

# Typography

> **Typography is the primary way FinTrack communicates information.**

---

# Purpose

This document defines the typography system used throughout FinTrack.

Typography establishes hierarchy, improves readability, and helps users identify important information without conscious effort.

Typography should communicate structure before color or decoration.

---

# Font Family

## Primary Font

**Inter**

Inter should be used for all interface elements, including:

* Headings
* Body text
* Buttons
* Inputs
* Tables
* Navigation
* Charts
* Cards

---

## Fallback Stack

```css
font-family:
"Inter",
system-ui,
-apple-system,
BlinkMacSystemFont,
"Segoe UI",
sans-serif;
```

---

# Typography Principles

## Readability First

Choose readability over style.

Users should never struggle to read financial information.

---

## Consistent Hierarchy

Every text element must belong to a predefined typography scale.

Avoid arbitrary font sizes.

---

## Numbers Matter

Financial values are the most important content.

Large numbers should immediately attract attention.

Secondary descriptions should remain visually quiet.

---

# Font Scale

| Token      | Size | Weight | Line Height | Usage             |
| ---------- | ---: | -----: | ----------: | ----------------- |
| Display    | 48px |    700 |        56px | Hero totals       |
| H1         | 36px |    700 |        44px | Page titles       |
| H2         | 30px |    700 |        38px | Section titles    |
| H3         | 24px |    600 |        32px | Card titles       |
| H4         | 20px |    600 |        28px | Subsections       |
| Body Large | 18px |    400 |        28px | Important content |
| Body       | 16px |    400 |        24px | Default text      |
| Body Small | 14px |    400 |        20px | Supporting text   |
| Caption    | 12px |    500 |        18px | Labels, metadata  |

---

# Font Weights

Only four weights should be used.

| Weight | Usage                          |
| -----: | ------------------------------ |
|    400 | Body text                      |
|    500 | Labels                         |
|    600 | Section headings               |
|    700 | Hero values and major headings |

Avoid using additional weights unless there is a documented reason.

---

# Hero Numbers

The dashboard's key financial metrics should use the Display style.

Examples:

* Monthly Spend
* Remaining Budget
* Savings
* Income

These values should always be the most visually prominent elements on the screen.

---

# Text Hierarchy

The order of visual importance is:

1. Hero values
2. Page title
3. Section heading
4. Primary content
5. Supporting information
6. Metadata

No secondary text should compete visually with financial summaries.

---

# Text Alignment

Use left alignment by default.

Exceptions:

* Numeric values in tables may be right-aligned.
* Currency columns should be right-aligned for easy comparison.

Avoid centered paragraphs.

---

# Numbers and Currency

Financial values should:

* Use tabular numerals where supported.
* Include the configured currency symbol.
* Follow the Indian numbering system.

Examples:

```text
₹180

₹1,250

₹12,500

₹1,23,456

₹12,34,567
```

Consistency is mandatory across the application.

---

# Text Colors

Typography should use semantic color tokens only.

| Purpose        | Token          |
| -------------- | -------------- |
| Primary text   | Text Primary   |
| Secondary text | Text Secondary |
| Metadata       | Text Muted     |
| Success        | Success        |
| Warning        | Warning        |
| Error          | Danger         |

Never hardcode text colors.

---

# Links

Links should be visually distinct but understated.

Rules:

* Underline only on hover or focus.
* Use the Primary token.
* Avoid long paragraphs containing multiple links.

---

# Buttons

Button labels should use:

* Size: 16px
* Weight: 600
* Letter spacing: 0

Text should remain sentence case.

Avoid ALL CAPS.

---

# Inputs

Input text:

* Size: 16px
* Weight: 400

Placeholder text should use the Text Muted token.

---

# Tables

Table headers:

* 14px
* Weight 600

Table values:

* 16px
* Weight 400

Financial values should align consistently.

---

# Charts

Chart labels should never dominate the visualization.

Use:

* 12px–14px
* Weight 500

Large chart titles should use H3.

---

# Accessibility

Minimum body text size:

**16px**

Avoid smaller body text.

Contrast must satisfy WCAG AA requirements.

Typography should remain readable at browser zoom levels up to 200%.

---

# Responsive Rules

Typography should scale naturally.

Display text may reduce on smaller screens.

Body text should remain at 16px for readability.

Avoid creating separate typography systems for desktop and mobile.

---

# Implementation Rules

Do not use arbitrary font sizes.

Incorrect:

```css
font-size: 17px;
```

Correct:

```css
font-size: var(--font-body);
```

All typography values should reference design tokens.

---

# Definition of Done

Typography implementation is complete when:

* Only approved font sizes are used.
* Only approved weights are used.
* Financial values follow the Indian numbering system.
* Semantic color tokens are used.
* Typography hierarchy remains consistent across all screens.

---

# Closing

Typography should quietly organize information.

Users should understand the importance of information before they consciously read it.

That is the purpose of the FinTrack typography system.
