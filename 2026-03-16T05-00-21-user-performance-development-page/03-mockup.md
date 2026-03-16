## Overview

A new set of pages for downloading performance development reports, with role-based access control. Admins can download all report types for any user in the system, with bulk ZIP download filtered by company. Supervisors and mentors see only their subordinates and mentees, and the report types available to them can be restricted through an access control configuration page.

![Admin Download Page](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-16T05-00-21-user-performance-development-page/03-r1-mockup-admin-download.png)
[Open mockup](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-16T05-00-21-user-performance-development-page/03-r1-mockup-admin-download.html)

![Supervisor / Mentor Download Page](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-16T05-00-21-user-performance-development-page/03-r1-mockup-supervisor.png)
[Open mockup](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-16T05-00-21-user-performance-development-page/03-r1-mockup-supervisor.html)

![Report Access Control Page](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-16T05-00-21-user-performance-development-page/03-r1-mockup-access-control.png)
[Open mockup](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-16T05-00-21-user-performance-development-page/03-r1-mockup-access-control.html)

### Layout Notes

- Entry point: a new "Download Reports" section in the Performance Development navigation, visible to admins, supervisors, and mentors — each sees the appropriate scoped view
- Report type columns (Annual Targets, Self Assessment, Feedback, Competency Evaluation) can be toggled in the filter bar to control what is included in downloads
- "Download selected as ZIP" becomes active once at least one user row is checked; it packages all enabled report types for all checked users into a single archive
- Individual per-row download buttons allow downloading reports for a single user without needing bulk selection
- On the Supervisor / Mentor page the user list is automatically scoped to the viewer's subordinates and mentees — no company filter is shown
- Report type columns restricted for the viewer's role are hidden entirely, so supervisors and mentors never see report types they are not permitted to access
- The Access Control page is accessible to admins only via the "Configure access" link in the page toolbar
- Access control is configured per role (Supervisor, Mentor) and per report type — changes apply to all users in that role immediately
