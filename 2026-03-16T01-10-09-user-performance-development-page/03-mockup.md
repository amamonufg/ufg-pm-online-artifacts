## Original Request

Here is how user performance development page looks like.

![%D0%B8%D0%B7%D0%BE%D0%B1%D1%80%D0%B0%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5.webp](https://trello.com/1/cards/69b37e0e99c97f1344b8614a/attachments/69b37e22deffdc5c2867b71c/previews/69b37e23deffdc5c2867b72d/download/%D0%B8%D0%B7%D0%BE%D0%B1%D1%80%D0%B0%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5.webp)

We need a resonable way to download user's reports:

1. Admins should be able to download all reports (annual targets, self assessments, feedback, competency evaluation) for every user in the system.
2. Supervisors or mentors should be able to download all reports (annual targets, self assessments, feedback, competency evaluation) for every mentee or subordinate that they have.
3. There should be a way to limit / restrict which reports supervisors or mentors have access to. Let's say we only want to allow mentors and supervisors to download self assessments and feedback reports.
4. There should be bulk download option (select users from specific company: Altus Capital, Family Office, etc), select all / certain users and download all reports as zip archive.

Can you suggest a page design (or several pages, for example one for admins and supervisors / mentors and one for rights configuration) that would fit this criteria?

## Overview

A dedicated **Download Reports** section for the Performance Development module, allowing admins, supervisors, and mentors to download performance reports as individual PDFs or bulk ZIP archives.

Three pages are proposed:

- **Admin Download Page** — full access to all users and all report types, with company/department filters and bulk selection.
![Admin Download Page](https://trello.com/1/cards/69b75594fbed913f2bfe34a5/attachments/69b759c6842ae1ad383230a6/download/mockup-admin-download.png)

- **Supervisor / Mentor Download Page** — scoped to the user's own subordinates and mentees, with report type availability controlled by the access policy.
![Supervisor Download Page](https://trello.com/1/cards/69b75594fbed913f2bfe34a5/attachments/69b759cc5e1741b446e30714/download/mockup-supervisor-download.png)

- **Report Access Control** — admin-only configuration grid controlling which report types each role (Direct Supervisor, Indirect Supervisor, Mentor) may download.
![Report Access Control](https://trello.com/1/cards/69b75594fbed913f2bfe34a5/attachments/69b759d2df5fa5eb5688a0e1/download/mockup-access-control.png)

### Layout Notes

- Entry point: a "Download Reports" link added to the Performance Development navigation, visible based on the user's role
- The Admin Download page shows all users system-wide; the Supervisor/Mentor page shows only people assigned to the current user as subordinates or mentees
- Company and department dropdowns narrow the user list; the year dropdown determines which assessment cycle's reports are included
- Report type checkboxes appear above the table; on the supervisor page, restricted types appear greyed out with a "Restricted" chip
- A "Select all" checkbox in the table header selects all visible rows; a separate link selects all users matching the current filter (across pages)
- The "Download ZIP" button is enabled only when at least one user and at least one report type are selected; a badge on the button shows the count of selected users
- Each row also has a "Single" download button to download one user's reports directly
- The Access Control page is accessible to admins only; changes to toggles apply immediately system-wide; supervisors and mentors see the effect the next time they open the Download Reports page
