# UI Research: Performance Development Report Download

## Module
`assessment360` — Performance Development

## Reference Pages

### Pdp360Page (Primary Reference)
- **Path:** `src/pages/assessment360/pdp360/containers/Pdp360Page.tsx`
- **Layout:** Multi-tab report viewer with role-based user selection
- **Components used:** AppLayout, Dropdown, TabsContainer, Card, RadioButtons, Label, UserChip
- **Patterns noted:**
  - Feature-based conditional rendering (`isSupervisor` flag determines visible tabs)
  - User impersonation for supervisors viewing subordinates
  - Tab-based organization: Annual Targets, Self Assessment, Feedback, Competency Evaluation, Summary
  - Mentor/Supervisor relationship display with role labels

### AssessmentReportPage (Secondary Reference)
- **Path:** `src/pages/assessment360/assessmentReport/containers/AssessmentReportPage.tsx`
- **Layout:** Single entity report viewer with selector toolbar
- **Components used:** AppLayout, Dropdown, Button, TabsContainer, Skeleton
- **Patterns noted:**
  - Role-based user list filtering: admin sees all, supervisor sees subordinates only
  - Dynamic user options based on `user.features.some(FEATURE.assessment360.reportAdmin)`

### FeaturesPage (Permissions Reference)
- **Path:** `src/pages/hrs/features/containers/FeaturesPage.tsx`
- **Layout:** Hierarchical feature tree with staff assignment
- **Components used:** AdminPage, AdminFilterRow, FilterText, FilterAutocomplete, DropdownList, Modal, Label, ConfirmButton
- **Patterns noted:**
  - Tree structure for hierarchical permissions with expand/collapse
  - Staff autocomplete for granting features
  - In-place grant/revoke with confirmation

## Similar Patterns

- **Download Export** — `DownloadTimesheetsButton.tsx` — builds query string → LinkButton to API endpoint
- **AdminPage with Bulk Actions** — `src/components/AdminPage/` — `canSelectRows`, `onRowSelectionChange`
- **Role-Based Access Control** — `AssessmentReportPage.tsx` — `FEATURE.assessment360.*` flags
- **Multi-Select Autocomplete** — `FeaturesPage.tsx` — `FilterAutocomplete({ isMulti: true })`

## Components Needed

- **Checkbox** — `src/components/Checkbox` — row selection, indeterminate "select all"
- **Table** — `src/components/Table` — `canSelectRows`, `onRowSelectionChange`
- **Modal** — `src/components/Modal` — report type selection, confirmation dialogs
- **Dropdown / FilterAutocomplete** — `src/components/Dropdown` + `src/components/Filter` — company/user multi-select
- **AdminFilterRow** — `src/components/Filter` — filter bar above table
- **Button / LinkButton** — `src/components/Button` — download actions
- **Card** — `src/components/Card` — section containers
- **Label** — `src/components/Labels` — role badges, report type tags
- **TabsContainer** — `src/components/Tabs` — separate admin vs supervisor interfaces

## Image Observations

The Trello screenshot URL was inaccessible. Based on the card description, the current performance development page likely shows:
- User/assessment selector at the top
- Tab-based organization of report types (Annual Targets, Self Assessment, Feedback, Competency Evaluation)
- Role-based tab visibility (supervisors see limited tabs)

## Design Recommendations

**Three pages / sections:**

1. **Admin Report Download** — Full access, all users, all report types, bulk ZIP download
   - Filter bar (company + user multi-select) → Table with row selection → Download toolbar

2. **Supervisor/Mentor Report Download** — Role-filtered users, restricted report types
   - Role info panel → Subordinates checklist → Pre-configured (restricted) report types → Download

3. **Report Access Control** (admin only) — Configure which roles can download which reports
   - Hierarchical tree: Role → Report Type → Allowed users, with in-place grant/revoke
