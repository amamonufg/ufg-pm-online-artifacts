## UI Research

### Module
Assessment 360 — Performance Development

### Reference Page
- **Path:** src/pages/assessment360/pdp360/containers/Pdp360Page.tsx
- **Layout:** Tabbed detail page with role-based access control
- **Components used:** TabsContainer/Tab, Dropdown, Button, LinkButton, Labels, Modal, AdminTable, AdminFilterRow
- **Patterns noted:**
  - Multiple tabs: Annual targets, Self assessment, Feedback, Competency evaluation, Summary
  - User selection strip with avatar chips and role labels (You, Supervisor, Mentor, Subordinate)
  - Assessment period selector dropdown with Active/Inactive status labels
  - Permission-based tab visibility — supervisors see restricted view
  - Download report and Send to supervisor action buttons in card header

### Similar Patterns
- Single report download with filtered query string — `src/pages/assessment360/assessmentProgressReport/containers/AssessmentProgressReportPage.tsx`
- Bulk ZIP download with filter-based filename — `src/pages/invoice/containers/InvoicePage.tsx`
- Table row selection with checkboxes for bulk operations — `src/components/Table/RowSelectColumn.tsx` (`useRowSelectColumn` hook)

### Components Needed
- **AdminPage / AdminTable / AdminFilterRow** — `src/components/AdminPage`
- **FilterSelect** (isMulti) — `src/components/Filter`
- **FilterAutocomplete** — `src/components/Filter`
- **LinkButton** — `src/components/Link`
- **Label** — `src/components/Labels`
- **Checkbox** — `src/components/Checkbox`
- **AppLayout** — `src/components/Layout`

### Image Observations
- Page header: Assessment dropdown (e.g. "2025 Active"), three date range period indicators — active one highlighted
- User selection strip: avatar chips with name and role label (You, Subordinate) for switching whose data is viewed
- Tab navigation: Annual targets | Self assessment | Feedback | Competency evaluation | Summary
- Content card: "Business & Personal Development Goals" with Download report (dark) and Send report to supervisor (green) buttons top right
- Empty state: warning triangle icon inside light grey rounded panel
- Edit button (outlined, small) at bottom left of card
