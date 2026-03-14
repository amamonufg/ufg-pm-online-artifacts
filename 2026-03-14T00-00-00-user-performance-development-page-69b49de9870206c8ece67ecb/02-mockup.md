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

A dedicated Performance Reports page that lets administrators download reports for all staff, and supervisors/mentors download reports for their own direct reports and mentees. A separate admin-only configuration page controls which report types each role can access.

**Views:**
- ![Admin Download Page](https://trello.com/1/cards/69b49de9870206c8ece67ecb/attachments/69b4b56494919ede5d8fbb77/download/mockup-admin-download.png)
- ![Supervisor/Mentor Download Page](https://trello.com/1/cards/69b49de9870206c8ece67ecb/attachments/69b4b56e4669dbc4d1d373de/download/mockup-supervisor-download.png)
- ![Access Control Configuration](https://trello.com/1/cards/69b49de9870206c8ece67ecb/attachments/69b4b5767507de2c538ec7d9/download/mockup-access-control.png)

### Layout Notes

- Entry point: Performance Reports item in the navigation, accessible from the Performance section
- Admins see all staff across all companies; the Company filter lets them narrow down by entity, and a Report Type filter further scopes the visible columns
- Supervisors and mentors see only their own direct reports and mentees; the Company filter is replaced by a Show filter (direct reports, mentees, or both); a blue info banner at the top explains the scope and mentions that some report types may be restricted
- Report type columns show a green checkmark when a report exists for the selected year, or a grey dash when it does not
- For supervisors/mentors, columns for restricted report types show "Restricted" in grey italic text; the column header is greyed out and shows a lock icon; restricted cells cannot be selected for bulk download
- The Download Selected button in the toolbar is disabled until at least one user row is checked; once active it shows the count of selected users in parentheses
- Download All downloads all currently visible users in the filtered list without requiring individual row selection; the count reflects the current filter
- Each row has an individual Download button that packages all available and permitted reports for that person as a zip archive
- The Access Control page is admin-only and presents a matrix: report types as rows, roles (Supervisors, Mentors) as columns, with a checkbox at each intersection
- A Visibility Scope section below the matrix shows read-only information confirming that supervisors see direct reports only and mentors see mentees only
- Changes to access control take effect immediately for all users with the affected role; a warning banner at the top of the page communicates this clearly
