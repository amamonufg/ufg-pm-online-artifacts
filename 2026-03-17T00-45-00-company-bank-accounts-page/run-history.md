## User Prompt

![https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T00-45-00-company-bank-accounts-page/01-user-prompt-image-01.png](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T00-45-00-company-bank-accounts-page/01-user-prompt-image-01.png)

On the company bank accounts page following changes are proposed:

1. Rename Company Bank Fccounts → Internal Company Bank Accounts (header, nav menu title, where applicable)
2. Add account number field
3. Render company name value in company column (now shows company short code)
4. Adjust column order: 1) Company (renders company name), 2) Company Code (renders company short code), 3) Bank name, 4) Account name, 5) Account short code, 6) Account currency, 7) Account number, 8) IBAN, 9) Status, 10) Actions.

![https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T00-45-00-company-bank-accounts-page/01-user-prompt-image-02.png](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T00-45-00-company-bank-accounts-page/01-user-prompt-image-02.png)

On the company bank account form page following changes are proposed:

1. Add new field - Correspondent account
2. Change field order: 1) Company, 2) Bank name, 3) Account name, 4) Short code, 5) Account currency, 6) Account number, 7) Correspondent account number, 8) IBAN, 9) SWIFT, 10) Address, 11) Active flag
3. Instead of having active flag (which just reflects account state), we need a way to indicate several states that can happen to bank account: 1) account termination (with termination date and notes), 2) account suspension / block (with block date and notes), 3) account suspension lifted / block removed.

---

## UI Research

### Module
`treasury/companyBank`

### Reference Page
- **Path:** `src/pages/treasury/companyBank/containers/CompanyBankPage.tsx`
- **Layout:** AdminPage with table and modal form
- **Components used:** AdminPage, AdminTable, AdminForm, Label, formText, formTextarea, formAutocomplete, formCheckbox, FilterRadioButtons
- **Patterns noted:**
  - TABLE_CONFIG array with `TableColumn<T>[]` defining columns with Header and Cell properties
  - FORM_CONFIG array with `FormFieldConfig<T>[]` with key, label, widget, validate
  - FILTER_CONFIG with search, select dropdowns, and radio button filters
  - `formAutocomplete` for entity references (company, currency)
  - `Label` component with variant (success/danger) for status display
  - Custom Cell renderer using `props.row.original` and `props.value`
  - `toSubmitBody()` transforms form data before API submission
  - `formatModalTitle()` formats modal header with shortCode + accountName

### Similar Patterns
- VendorBank page (nearly identical structure, already has `corrAccountNumber`, `corrBankName`, `corrBankSwift`) — `src/pages/treasury/vendorBank/containers/VendorBankPage.tsx`
- BudgetLineCategory page uses `FilterRadioButtons` for multi-option filtering — `src/pages/admin/budgetLineCategory/containers/BudgetLineCategoryPage.tsx`

### Components Needed
- **AdminPage, AdminTable, AdminForm** — `src/components/AdminPage`
- **Label** — `src/components/Labels/Label.tsx`
- **formText, formTextarea, formAutocomplete** — `src/components/Form/Widgets`
- **formSelect** — `src/components/Form/Widgets/FormSelect.tsx`
- **RadioButtons** — `src/components/Radio`
- **FilterRadioButtons** — `src/components/Filter`
- **Table, TableColumn** — `src/components/Table/types.ts`

### Image Observations
- **Image 1 (List page):** Header "Company Bank Accounts". Columns: Short Code, Account Name, Bank Name, Currency, IBAN, Company, Status, Actions. Status uses Label component (green=Active, red=Inactive). Company column shows company name with ID in parentheses. Filters: search, Bank Name dropdown, Company ID dropdown, Currency dropdown, Status radio (All/Active/Inactive). 20 of 525 records shown. Account Number column is absent.
- **Image 2 (Form page):** Modal form. Visible fields: Short Code, Account Name, Bank Name, Company (autocomplete), Account Currency (autocomplete), Address (textarea), SWIFT, Account Number. Single-column layout. Save/Close at bottom. Active flag as checkbox. Correspondent account field absent. Field order needs resequencing.

---

## Revision 1

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
