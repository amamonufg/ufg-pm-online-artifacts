## UI Research

### Module
assessment360 (Performance Development / Staff Reports)

### Reference Page
- **Path:** src/pages/assessment360/assessmentProgressReport/containers/AssessmentProgressReportPage.tsx
- **Layout:** Admin list page with filter row above table and download button in toolbar
- **Components used:** AppLayout, AdminPage, AdminFilterRow, AdminTable, useAdminPageContext, FilterAutocomplete, FilterSelect, FilterRadioButtons, LinkButton, Label, toQueryString
- **Patterns noted:**
  - Download via `LinkButton` (external, newTab) with URL built from `toQueryString(filter)` — e.g. `/api/endpoint/download/filename.xlsx?${qs}`
  - Company multi-select filter using `FilterSelect({ isMulti: true })`
  - Feature-gated page access via `AppLayout` `feature` prop
  - `AdminFilterRow` renders a collapsible filter panel above the table
  - `AdminTable` with custom `Cell` renderers per column (BooleanCell, DateBooleanTableCell)
  - `useAdminPageContext` to access current filter state inside toolbar/cell components

### Rights Configuration Reference
- **Path:** src/pages/hrs/features/containers/FeaturesPage.tsx
- **Layout:** Admin page with expandable feature tree; each row shows which staff have that feature
- **Patterns noted:**
  - `FeatureStaffCell` — label chips per assigned user + dropdown to add users (`DropdownList`)
  - `VariableFeatureStaffCell` — modal form to configure per-user variable features
  - `ConfirmButton` with trash icon for revoking feature from a user
  - Company + Staff multi-select filters to scope the view
  - `grantFeature` / `revokeFeature` / `bulkUpdateFeature` API calls

### Similar Patterns
- Feature/rights assignment per user — `src/pages/hrs/features/containers/FeaturesPage.tsx`
- Staff list download with company/business-unit filters — `src/pages/hrs/staff/containers/StaffPage.tsx`
- Role-gated sections via `<Feature code={[FEATURE.admin.staff]} fallback={<Forbidden />}>` — `src/pages/hrs/staff/containers/StaffPage.tsx`

### Components Needed
- **AdminPage** — `src/components/AdminPage`
- **AdminFilterRow** — `src/components/AdminPage`
- **AdminTable** — `src/components/AdminPage`
- **AppLayout** — `src/components/Layout`
- **FilterAutocomplete** — `src/components/Filter` (company multi-select, staff multi-select)
- **FilterSelect** — `src/components/Filter`
- **LinkButton** — `src/components/Link` (download trigger)
- **Modal / ModalContext** — `src/components/Modal` (rights config dialog)
- **Form** — `src/components/Form`
- **Button / ConfirmButton** — `src/components/Button`
- **Label** — `src/components/Labels`
- **DropdownList** — `src/components/Dropdown` (user assignment in rights config)
- **Checkbox** — `src/components/Checkbox` (bulk row selection)
- **Tabs / TabsContainer** — `src/components/Tabs` (admin vs supervisor view switch)

### Image Observations
- Image could not be loaded (Trello authentication required)
- Card description references an existing performance development page as visual context
- The feature requires two distinct views: admin (all users/all companies) and supervisor/mentor (subordinates only)
- Report types in scope: annual targets, self assessments, feedback, competency evaluation
- Bulk download: filter by company → select users → download all selected reports as a single ZIP archive
- A separate rights/configuration page controls which report types supervisors and mentors are allowed to download
