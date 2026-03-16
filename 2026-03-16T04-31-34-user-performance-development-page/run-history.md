## User Prompt

Here is how user performance development page looks like.

![%D0%B8%D0%B7%D0%BE%D0%B1%D1%80%D0%B0%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5.webp](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-16T04-31-34-user-performance-development-page/01-user-prompt-image-01.png)

We need a resonable way to download user's reports:

1. Admins should be able to download all reports (annual targets, self assessments, feedback, competency evaluation) for every user in the system.
2. Supervisors or mentors should be able to download all reports (annual targets, self assessments, feedback, competency evaluation) for every mentee or subordinate that they have.
3. There should be a way to limit / restrict which reports supervisors or mentors have access to. Let's say we only want to allow mentors and supervisors to download self assessments and feedback reports.
4. There should be bulk download option (select users from specific company: Altus Capital, Family Office, etc), select all / certain users and download all reports as zip archive.

Can you suggest a page design (or several pages, for example one for admins and supervisors / mentors and one for rights configuration) that would fit this criteria?

---

## UI Research

### Module
assessment360

### Reference Page
- **Path:** src/pages/assessment360/assessmentProgressReport/containers/AssessmentProgressReportPage.tsx
- **Layout:** list/table page with filter row and toolbar download button
- **Components used:** AdminPage, AdminTable, AdminFilterRow, FilterAutocomplete, FilterSelect, FilterRadioButtons, LinkButton
- **Patterns noted:**
  - Assessment selector (FilterAutocomplete) used to scope data before loading
  - Company multi-select filter (FilterSelect isMulti)
  - Download button in toolbar built from context filters — generates query string for Excel download URL
  - Boolean flag filters (FilterRadioButtons) to show All / Yes / No
  - Table with company, user columns and status indicators

### Similar Patterns
- Report download with filter-driven URL — toolbar LinkButton builds download URL from active filter state — `src/pages/assessment360/assessmentProgressReport/containers/AssessmentProgressReportPage.tsx`
- Multi-user selector strip with avatar thumbnails for subordinates — `src/pages/assessment360/pdpSummary/containers/PersonalDevelopmentPlanPage.tsx`
- Admin table page with company filter and per-row actions — `src/pages/hrs/professionalDevelopment/containers/ProfessionalDevelopmentPage.tsx`

### Components Needed
- **AdminPage / AdminTable / AdminFilterRow / AdminToolbar** — `src/components/AdminPage`
- **FilterAutocomplete** — `src/components/Filter`
- **FilterSelect** (isMulti) — `src/components/Filter`
- **FilterRadioButtons** — `src/components/Filter`
- **LinkButton** — `src/components/Link`
- **Label** — `src/components/Labels`
- **Checkbox** — `src/components/Checkbox`
- **AppLayout** — `src/components/Layout`

### Image Observations
- Page has a top bar with Assessment year selector (dropdown, e.g. "2025 Active") and three period indicators: Objectives setting, Mid year, End year — the active one is highlighted
- Horizontal user strip below shows avatar thumbnails with name and role label ("You", "Subordinate") — allows switching whose data is being viewed
- Tab navigation: Annual targets | Self assessment | Feedback | Competency evaluation | Summary
- Content area shows a card titled "Business & Personal Development Goals" with "Download report" (dark) and "Send report to supervisor" (green) buttons top right
- Empty state uses warning triangle icon inside a light grey rounded panel
- Edit button (outlined, small) at bottom left of the card

---

## Revision 1

A new set of pages for downloading performance development reports, with role-based access control. Admins can download all report types for any user in the system, with bulk ZIP download filtered by company. Supervisors and mentors see only their subordinates and mentees, and the report types available to them can be restricted through an access control configuration page.

**Views:**
- [Admin Download Page](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-16T04-31-34-user-performance-development-page/mockup-admin-download.html)
- [Supervisor / Mentor Download Page](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-16T04-31-34-user-performance-development-page/mockup-supervisor.html)
- [Report Access Control Page](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-16T04-31-34-user-performance-development-page/mockup-access-control.html)

### Layout Notes

- Entry point: a new "Download Reports" section in the Performance Development navigation, visible to admins, supervisors, and mentors — each sees the appropriate scoped view
- Report type columns (Annual Targets, Self Assessment, Feedback, Competency Evaluation) can be toggled in the filter bar to control what is included in downloads
- "Download selected as ZIP" becomes active once at least one user row is checked; it packages all enabled report types for all checked users into a single archive
- Individual per-row download buttons allow downloading reports for a single user without needing bulk selection
- On the Supervisor / Mentor page the user list is automatically scoped to the viewer's subordinates and mentees — no company filter is shown
- Report type columns restricted for the viewer's role are hidden entirely, so supervisors and mentors never see report types they are not permitted to access
- The Access Control page is accessible to admins only via the "Configure access" link in the page toolbar
- Access control is configured per role (Supervisor, Mentor) and per report type — changes apply to all users in that role immediately
