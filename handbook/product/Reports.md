---
title: Reports
category: Product
status: Approved
version: 1.0
owner: Product
depends_on:
  - Dashboard
  - Transactions
  - Budgets
  - Analytics
related:
  - Export
  - Settings
---

# Reports

> **Reports provide a permanent summary of financial activity over a defined period.**

---

# Purpose

The Reports feature generates structured financial summaries that users can review, export, print, or archive.

Unlike Analytics, which is designed for exploration, Reports present finalized information for a selected time period.

Reports should remain consistent and reproducible.

---

# User Goals

Users visit Reports to:

* Review monthly spending.
* Compare periods.
* Export financial summaries.
* Archive historical data.
* Share reports when required.

Reports should prioritize completeness and clarity.

---

# Screen Layout

```text
┌────────────────────────────────────────────────────────────────────────────┐
│ Reports                                              July 2026 ▼           │
├────────────────────────────────────────────────────────────────────────────┤
│ Report Type • Date Range • Export                                  Create │
├────────────────────────────────────────────────────────────────────────────┤
│ Summary Cards                                                          │
├────────────────────────────────────────────────────────────────────────────┤
│ Spending by Category                                                   │
├────────────────────────────────────────────────────────────────────────────┤
│ Income vs Expenses                                                     │
├────────────────────────────────────────────────────────────────────────────┤
│ Budget Performance                                                     │
├────────────────────────────────────────────────────────────────────────────┤
│ Report Table                                                           │
└────────────────────────────────────────────────────────────────────────────┘
```

---

# Report Types

Version 1 supports:

| Report             | Purpose                      |
| ------------------ | ---------------------------- |
| Monthly Summary    | Overview of one month        |
| Category Summary   | Spending grouped by category |
| Income vs Expense  | Financial balance            |
| Budget Report      | Budget performance           |
| Transaction Report | Complete transaction history |

Each report should be generated from the selected time period.

---

# Report Filters

Users may specify:

* Month
* Date Range
* Category
* Transaction Type

Filters should remain consistent with Analytics.

---

# Monthly Summary

Display:

* Total Income
* Total Expenses
* Net Savings
* Largest Category
* Average Daily Spend
* Total Transactions

This report provides a quick overview of financial health.

---

# Category Summary

Display:

* Category
* Total Amount
* Percentage
* Number of Transactions

Sort by highest spending.

---

# Income vs Expense

Display:

* Total Income
* Total Expenses
* Net Savings
* Savings Rate

Include a simple comparison chart.

---

# Budget Report

Display:

* Monthly Budget
* Actual Spending
* Remaining Budget
* Categories Over Budget

Highlight only meaningful deviations.

---

# Transaction Report

Display a complete transaction table for the selected period.

Columns:

* Date
* Merchant
* Category
* Type
* Amount
* Notes

This serves as the authoritative financial record.

---

# Report Generation

Generating a report should:

1. Apply current filters.
2. Calculate summary metrics.
3. Render the report.
4. Enable export options.

The generated report should remain stable until filters change.

---

# Export

Version 1 supports:

* CSV
* PDF

Exports should faithfully match the generated report.

Formatting should remain consistent across export formats.

---

# User Flows

## Generate Monthly Report

```text
Reports

↓

Select Month

↓

Generate Report

↓

Review Summary

↓

Export (optional)
```

---

## Export Report

```text
Reports

↓

Generate

↓

Export

↓

Download
```

---

# Business Rules

* Reports are read-only.
* Reports always reflect the selected time period.
* Exported reports should preserve totals and formatting.
* Regenerating a report replaces the previous view.

---

# Empty State

Display:

```text
No data available for the selected period.

Try another date range or record more transactions.
```

---

# Loading State

Display:

* Summary skeletons.
* Chart placeholders.
* Table skeleton.

Maintain the final report layout.

---

# Error State

Display:

```text
Unable to generate the report.

Please try again.
```

Provide a Retry action.

---

# Performance Expectations

Reports should:

* Generate within two seconds for typical datasets.
* Export within five seconds for common report sizes.
* Scale to several years of historical transactions.

---

# Accessibility

Reports must:

* Use semantic headings.
* Provide accessible table markup.
* Include text summaries for charts.
* Preserve accessibility in exported PDF where practical.

---

# Acceptance Criteria

The Reports feature is complete when:

* Users can generate each report type.
* Filters apply consistently.
* Summary metrics are accurate.
* Exports match the displayed report.
* Empty, loading, and error states are implemented.
* Accessibility requirements are satisfied.

---

# Future Enhancements

Future versions may introduce:

* Quarterly reports.
* Annual financial summaries.
* Tax-ready reports.
* Scheduled report generation.
* Email delivery.
* AI-generated report narratives.

These enhancements should build upon the reporting framework without changing its core purpose.

---

# Goal

Reports should provide a reliable historical record of a user's finances.

Unlike Analytics, which encourages exploration, Reports should provide confidence that the numbers are complete, accurate, and ready to review or share.
