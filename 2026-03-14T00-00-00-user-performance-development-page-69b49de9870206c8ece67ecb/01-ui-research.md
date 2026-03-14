## UI Research

### Module
Assessment360 / Performance

### Reference Page
- **Path:** src/pages/hrs/professionalDevelopment/containers/ProfessionalDevelopmentPage.tsx
- **Layout:** admin list page with bulk selection
- **Components used:** AdminPage, AdminTable, AdminToolbar, AdminFilterRow, Checkbox, Dropdown, Button, Labels
- **Patterns noted:**
  - AdminPage pattern: toolbar + filter row + table + modal actions
  - Bulk row selection via RowSelectColumn checkbox
  - Filter row with company/entity dropdowns and search input
  - Primary action button in toolbar (Download Selected with count)
  - Row-level action buttons for single-item operations

### Similar Patterns
- Tabbed report viewer with user and assessment selectors — `src/pages/assessment360/assessmentReport/containers/AssessmentReportPage.tsx`
- Admin list with status labels and bulk toolbar actions — `src/pages/hrs/professionalDevelopment/containers/ProfessionalDevelopmentPage.tsx`

### Components Needed
- **AdminPage / AdminTable / AdminToolbar / AdminFilterRow** — `src/components/AdminPage`
- **Checkbox / RowSelectColumn** — `src/components/Checkbox`
- **Dropdown** — `src/components/Dropdown`
- **Button** — `src/components/Button`
- **Label / LabelInfo / LabelMuted** — `src/components/Labels`
- **Table / TableColumn / TableAction** — `src/components/Table`
- **Alert** — `src/components/Alert`

### Image Observations
- Image URL was inaccessible due to Trello authentication restriction — design based on card description text only
- Card references the existing user performance development page as a visual reference
