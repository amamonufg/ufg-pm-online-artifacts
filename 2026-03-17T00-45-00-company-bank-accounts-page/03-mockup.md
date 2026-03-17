The Internal Company Bank Accounts module receives two coordinated updates: a renamed list page with an expanded column set, and a redesigned form page with a richer account status model replacing the simple active/inactive checkbox.

On the list page, the header and navigation entry are updated from "Company Bank Accounts" to "Internal Company Bank Accounts" to distinguish internal accounts from vendor bank accounts. The column layout is reordered and expanded: the Company column now displays the full company name (previously it showed a short code), a new Company Code column carries the short code, and a new Account Number column is inserted before the IBAN column. The Status badge gains two new states — Suspended (amber) and Terminated (red) — alongside the existing Active (green) state. The status filter radio group is extended to match: All, Active, Suspended, Terminated.

On the form page, a new Correspondent Account Number field is added, and all fields are resequenced into a logical banking order. The previous Active checkbox is replaced by an Account Status section with four radio options: Active, Suspended / Blocked, Terminated, and Block Removed. Selecting any non-Active option reveals a contextual sub-form with a relevant date field (Block Date, Termination Date, or Removal Date) and a Notes textarea, allowing staff to record when and why the status changed.

![List Page](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T00-45-00-company-bank-accounts-page/03-r1-mockup-list.png)
[Open mockup](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T00-45-00-company-bank-accounts-page/03-r1-mockup-list.html)

![Form Page](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T00-45-00-company-bank-accounts-page/03-r1-mockup-form.png)
[Open mockup](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T00-45-00-company-bank-accounts-page/03-r1-mockup-form.html)

## Layout Notes

- The list page renders as a full content area with a filter bar above the table. The filter bar uses a horizontal row: search input on the left, then three dropdowns (Bank Name, Company, Currency), then status radio buttons flush to the right.
- The table has 10 columns. The Account Number and IBAN columns are fixed-width and may truncate with ellipsis on narrow viewports; a tooltip on hover reveals the full value.
- The Status badge uses three color variants: green for Active, amber/orange for Suspended, red for Terminated.
- The form renders as a modal dialog (centered overlay) with a single-column field layout. Fields are stacked vertically with consistent label-above-input layout.
- The Account Status section is visually separated from the banking fields by a section divider line and a bold section label. Radio options are listed vertically. The conditional sub-form (date + notes) slides in below the selected radio option, indented slightly to associate it with the selection.
- The conditional sub-form fields appear inline — no page reload or modal swap. When "Active" is selected, no sub-form is shown.
- Save and Cancel buttons are right-aligned at the bottom of the modal footer.
