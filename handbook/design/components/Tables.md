---
title: Tables
category: Design
status: Approved
version: 1.0
owner: Design
references:
  - Application-Shell.md
  - cards/Base-Card.md
  - ../foundation/Typography.md
  - ../foundation/Spacing.md
  - ../foundation/Colors.md
  - ../foundation/Borders-and-Radius.md
  - ../foundation/Accessibility.md
---

# Tables

> **Tables exist to verify information, not impress users.**

---

# Purpose

Tables display structured financial data where precision is more important than visual summarization.

In FinTrack, tables are primarily used for:

* Transactions
* Budget history
* Import previews
* Export previews
* Search results

Tables should prioritize clarity, consistency, and efficient scanning.

---

# Design Philosophy

A table should answer one question:

**"Can I quickly find and verify the information I'm looking for?"**

Every design decision should reduce visual noise.

Tables are not dashboards.

They are working tools.

---

# Design Principles

Every table should:

* Be easy to scan.
* Preserve alignment.
* Support keyboard navigation.
* Adapt gracefully to smaller screens.
* Handle large datasets efficiently.

---

# Standard Layout

```text
┌────────────────────────────────────────────────────────────────────────────┐
│ Date │ Merchant │ Category │ Amount │ Account │ Notes │
├────────────────────────────────────────────────────────────────────────────┤
│ Jul 1│ Swiggy   │ Food     │ ₹420   │ HDFC    │ Dinner│
│ Jul 2│ Uber     │ Travel   │ ₹260   │ UPI     │ Office│
│ Jul 3│ Salary   │ Income   │ ₹75,000│ Bank    │ July  │
└────────────────────────────────────────────────────────────────────────────┘
```

---

# Standard Columns

Version 1 transaction tables use:

| Column         | Required |
| -------------- | -------- |
| Date           | Yes      |
| Merchant       | Yes      |
| Category       | Yes      |
| Amount         | Yes      |
| Payment Method | Optional |
| Notes          | Optional |

Additional columns require a documented product decision.

---

# Row Height

| Size        | Height |
| ----------- | -----: |
| Compact     |   40px |
| Default     |   48px |
| Comfortable |   56px |

Default:

```text
48px
```

---

# Typography

Headers:

* Body Small
* Weight 600

Rows:

* Body
* Weight 400

Amounts should always use tabular numerals.

---

# Alignment

| Column         | Alignment |
| -------------- | --------- |
| Date           | Left      |
| Merchant       | Left      |
| Category       | Left      |
| Amount         | Right     |
| Payment Method | Left      |
| Notes          | Left      |

Currency columns are always right-aligned.

---

# Row States

Rows support:

* Default
* Hover
* Selected
* Focused

Hover should subtly highlight the row.

Selection should remain clearly distinguishable.

---

# Sorting

Supported columns:

* Date
* Amount
* Merchant
* Category

Sorting indicators should remain subtle.

Default sort:

Newest first.

---

# Filtering

Tables support filtering by:

* Date
* Category
* Merchant
* Amount
* Income / Expense

Filtering should update results immediately.

---

# Search

Search should operate in real time.

Supported fields:

* Merchant
* Notes
* Category

Search should never reload the page.

---

# Pagination

Version 1 default:

50 rows per page.

If fewer than 50 rows exist:

Do not display pagination controls.

---

# Sticky Header

Desktop:

Table headers remain visible while scrolling.

Mobile:

Headers may scroll normally.

---

# Empty State

Display:

```text
No transactions found.

Start by typing:

coffee 180
```

Provide a clear path to creating the first transaction.

---

# Loading State

Use skeleton rows.

Preserve:

* Table width.
* Column widths.
* Header.

Avoid layout shifts.

---

# Error State

Display:

```text
Unable to load transactions.

Please refresh or try again.
```

Errors should not remove table structure.

---

# Row Actions

Hover may reveal:

* Edit
* Duplicate
* Delete

Primary row content should remain readable.

Avoid permanently displaying action buttons for every row.

---

# Bulk Selection

Version 1 supports:

* Select individual rows.
* Select all visible rows.

Bulk actions:

* Delete
* Export
* Change Category

Bulk actions should appear only after rows are selected.

---

# Responsive Behavior

Desktop:

Standard table.

Tablet:

Hide low-priority columns.

Mobile:

Convert rows into stacked cards.

Do not force horizontal scrolling unless absolutely necessary.

---

# Accessibility

Tables must support:

* Keyboard navigation.
* Screen readers.
* Proper table semantics.
* Focus indicators.

Use semantic HTML:

```html
<table>
<thead>
<tbody>
```

Header cells should use:

```html
<th scope="col">
```

---

# Performance

Large datasets should support:

* Virtual scrolling (future).
* Efficient rendering.
* Stable sorting.

Rendering should remain smooth with at least 10,000 transactions.

---

# Anti-Patterns

Do not:

* Center numeric columns.
* Use zebra striping with high contrast.
* Place buttons inside every cell.
* Wrap currency values onto multiple lines.
* Allow inconsistent column ordering.

Consistency is essential for financial review.

---

# Implementation Tokens

```css
--table-row-height: 48px;
--table-header-height: 52px;

--table-cell-padding-x: var(--space-4);
--table-cell-padding-y: var(--space-3);

--table-border: var(--border-1);
```

---

# Definition of Done

A table implementation is complete when:

* Financial values align correctly.
* Sorting behaves consistently.
* Filtering updates immediately.
* Keyboard navigation is supported.
* Accessibility requirements are satisfied.
* Responsive behavior matches this specification.

---

# Implementation Notes

### Frontend

* Build a reusable `<Table />` component with configurable column definitions.
* Separate rendering logic from data fetching.
* Support optional row actions through composition.

### Backend

* Return paginated and sortable datasets.
* Support server-side filtering for large datasets.
* Maintain stable sort order across requests.

### AI Coding Agent

* Never create page-specific table implementations.
* Reuse the shared Table component.
* Keep formatting logic inside reusable column definitions.
* Always right-align monetary values.

---

# Future Considerations

Future versions may introduce:

* Column resizing.
* Saved table views.
* Drag-and-drop column ordering.
* Inline editing.
* Virtualized rendering.

These features should extend the base Table component without changing its core interaction model.

---

# Closing

Tables are the source of financial truth in FinTrack.

Users should be able to scan hundreds of transactions quickly, verify every value confidently, and trust that the information is presented consistently every time.
