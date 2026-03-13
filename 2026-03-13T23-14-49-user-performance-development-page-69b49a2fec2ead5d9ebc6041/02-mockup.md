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

A new section of the Performance Development module allowing admins, supervisors, and mentors to download staff performance reports. The feature covers individual and bulk ZIP downloads, a role-aware interface that restricts visibility to each user's allowed reports and team, and a configuration page for controlling which report types each role can access.

**Views:**
- Admin Download Page — ![Admin Download Page](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-13T23-14-49-user-performance-development-page-69b49a2fec2ead5d9ebc6041/mockup-admin-download.png)
- Supervisor / Mentor Download Page — ![Supervisor / Mentor Download Page](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-13T23-14-49-user-performance-development-page-69b49a2fec2ead5d9ebc6041/mockup-supervisor.png)
- Report Download Access Configuration — ![Report Download Access Configuration](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-13T23-14-49-user-performance-development-page-69b49a2fec2ead5d9ebc6041/mockup-access-control.png)

### Layout Notes

- **Entry point:** New "Download Reports" page in the Performance Development section, accessible from the admin navigation menu
- **Admin view:** Shows all staff across all companies; filters for Company (multi-select), Assessment Year, and Report Types (multi-select); each row shows which of the four report types are available for that user (Annual Targets, Self Assessment, Feedback, Competency Evaluation); individual per-row download button plus bulk "Download Selected as ZIP" and "Download All as ZIP" buttons in the toolbar
- **Supervisor / Mentor view:** Shows only the current user's direct reports and mentees; available report type columns are limited to those the role is permitted to access (configured separately); an info banner at the top lists which report types the user is allowed to download; rows with no available allowed reports show a disabled download button; each team member is labelled as "Direct report" or "Mentee" for relationship context
- **Access Control configuration page:** A table of the four report types, each with a "Roles with Download Access" column; Admins are always granted access (shown greyed-out and non-removable); Supervisors and Mentors can be added or removed per report type using role chips with an inline "+ Add role" button; changes take effect immediately for all users in that role
- **Bulk download:** Selecting users via row checkboxes and clicking "Download Selected (N) as ZIP" triggers a ZIP archive download; "Download All as ZIP" skips selection and exports all currently visible users
- **Report availability indicators:** Each report type cell shows a green check badge if the report exists for that user, or a muted dash if not yet submitted; the per-row download button is disabled when no downloadable reports exist within the selected types
