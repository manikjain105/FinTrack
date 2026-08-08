---
title: Import
category: Product
status: Approved
version: 1.0
owner: Product
depends_on:
  - Transactions
  - Tables
  - Modals
  - Toasts
related:
  - Export
  - Settings
  - Reports
---

# Import

> **Import helps users bring existing financial data into FinTrack safely and confidently.**

---

# Purpose

The Import feature allows users to add historical transaction data from external files into FinTrack.

Import should prioritize safety over speed.

No data should be permanently imported until the user has reviewed and confirmed the results.

---

# User Goals

Users use Import to:

* Migrate from another expense tracker.
* Import spreadsheet records.
* Restore previously exported data.
* Add historical spending data.
* Save time by avoiding manual entry.

---

# Supported File Types

Version 1 supports:

| Format        | Supported |
| ------------- | --------- |
| CSV           | Yes       |
| Excel (.xlsx) | No        |
| JSON          | No        |
| PDF           | No        |

CSV should be UTF-8 encoded.

---

# Entry Point

Import is available from:

```text
Settings

↓

Import Data
```

Future versions may expose additional shortcuts.

---

# Import Workflow

```text
Choose File

↓

Validate File

↓

Preview

↓

Resolve Issues

↓

Confirm Import

↓

Import Complete
```

Users should never skip the Preview step.

---

# Screen Layout

```text
┌──────────────────────────────────────────────────────────────┐
│ Import Transactions                                           │
├──────────────────────────────────────────────────────────────┤
│ Choose CSV File                                               │
├──────────────────────────────────────────────────────────────┤
│ Validation Summary                                            │
├──────────────────────────────────────────────────────────────┤
│ Preview Table                                                 │
├──────────────────────────────────────────────────────────────┤
│ Cancel                                   Import Transactions  │
└──────────────────────────────────────────────────────────────┘
```

---

# Required Fields

Each imported row must contain:

* Date
* Amount
* Category
* Type

Optional fields:

* Merchant
* Notes

Rows missing required fields should be flagged before import.

---

# Validation

Before importing:

Validate:

* File format.
* Required columns.
* Date format.
* Numeric amounts.
* Transaction type.
* Category values.

Validation should occur before any database changes.

---

# Preview

The preview displays:

* Parsed transactions.
* Validation errors.
* Warnings.
* Total number of rows.
* Number of valid rows.

Invalid rows should remain visible but clearly identified.

---

# Duplicate Handling

Version 1 should detect likely duplicates using:

* Date
* Amount
* Merchant

Users may:

* Skip duplicates.
* Import anyway.

Duplicate detection should be conservative to avoid false positives.

---

# Error Resolution

Common issues:

* Missing category.
* Invalid amount.
* Invalid date.
* Unknown transaction type.

Users should understand exactly which rows require attention.

---

# Import Confirmation

Before importing, display:

* Number of transactions.
* Number of warnings.
* Number of skipped rows.
* Estimated changes.

Import begins only after explicit confirmation.

---

# Successful Import

After completion:

Display:

* Transactions imported.
* Transactions skipped.
* Time completed.

Dashboard, Budgets, Analytics, and Reports should update immediately.

---

# User Flows

## Import Existing Spreadsheet

```text
Settings

↓

Import

↓

Choose CSV

↓

Preview

↓

Confirm

↓

Dashboard Updated
```

---

# Business Rules

* Import is additive.
* Existing transactions remain unchanged.
* Invalid rows are never imported.
* Import should be atomic where possible.
* Partial failures should be reported clearly.

---

# Empty State

Display:

```text
Choose a CSV file to begin importing your transactions.
```

---

# Loading State

Display:

* Upload progress.
* Validation progress.
* Import progress.

For large files, show progress where available.

---

# Error State

Display:

```text
Unable to import this file.

Please review the highlighted issues and try again.
```

Do not discard the uploaded file automatically.

---

# Accessibility

The Import feature must:

* Support keyboard navigation.
* Clearly announce validation results.
* Associate errors with specific rows.
* Preserve logical focus order.

---

# Performance Expectations

Import should:

* Validate before modifying data.
* Handle several thousand transactions efficiently.
* Preserve application responsiveness during processing.

---

# Acceptance Criteria

The Import feature is complete when:

* CSV files can be imported successfully.
* Validation occurs before import.
* Users can preview imported data.
* Invalid rows are reported clearly.
* Dashboard and analytics update after import.
* Empty, loading, and error states are implemented.
* Accessibility requirements are satisfied.

---

# Future Enhancements

Future versions may introduce:

* Excel (.xlsx) support.
* Bank statement import.
* Automatic column mapping.
* Intelligent category suggestions.
* Scheduled imports.
* Cloud storage integrations.

These enhancements should preserve the safe, review-first workflow established in Version 1.

---

# Goal

Import should make switching to FinTrack effortless.

Users should feel confident that their historical data will be validated, previewed, and imported accurately without unexpected changes.
