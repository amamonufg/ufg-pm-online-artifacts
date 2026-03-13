## Original Request

Here is how user performance development page looks like.

![%D0%B8%D0%B7%D0%BE%D0%B1%D1%80%D0%B0%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5.webp](https://trello.com/1/cards/69b37e0e99c97f1344b8614a/attachments/69b37e22deffdc5c2867b71c/previews/69b37e23deffdc5c2867b72d/download/%D0%B8%D0%B7%D0%BE%D0%B1%D1%80%D0%B0%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5.webp)

We need a reasonable way to download user's reports:

1. Admins should be able to download all reports (annual targets, self assessments, feedback, competency evaluation) for every user in the system.
2. Supervisors or mentors should be able to download all reports (annual targets, self assessments, feedback, competency evaluation) for every mentee or subordinate that they have.
3. There should be a way to limit / restrict which reports supervisors or mentors have access to. Let's say we only want to allow mentors and supervisors to download self assessments and feedback reports.
4. There should be bulk download option (select users from specific company: Altus Capital, Family Office, etc), select all / certain users and download all reports as zip archive.

Can you suggest a page design (or several pages, for example one for admins and supervisors / mentors and one for rights configuration) that would fit this criteria?

## Overview

The Reports Download feature introduces three distinct surfaces into the UFGPM application. The first is the **Admin Report Download** page, where administrators can filter by company and individual users, select any combination of report types, pick rows from a paginated user table, and trigger a bulk ZIP download. The second is the **Supervisor / Mentor Report Download** page, which presents the same download workflow but scoped to the viewer's direct subordinates and mentees only; the available report types are pre-filtered to whatever access level the administrator has configured, with locked-out types shown as greyed-out and non-interactive. The third is the **Report Access Control** page (admin-only), which gives administrators a hierarchical permission editor where each role group (Admin, Supervisor, Mentor) can have specific report types toggled on or off, with optional per-staff overrides via assignee chips.

![Visual Prototype](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/69b38b239812c9dc7de0d12f-user-performance-development-2026-03-14T00-00-00/02-mockup.png)

### Layout Notes

**Entry Points and Navigation**

The three surfaces live under a "Reports" section in the main left-hand navigation. Admins see all three menu items: "Download Reports", "My Team Reports", and "Access Control". Supervisors and mentors only see "My Team Reports". The "Access Control" item is hidden entirely for non-admin roles.

**Admin Report Download**

The page opens with a horizontal filter bar containing a Company multi-select autocomplete and a User multi-select autocomplete that cascades off the company selection. Below the filter bar is a row of Report Type checkboxes (Annual Targets, Self Assessment, Feedback, Competency Evaluation) with a "Select All" toggle. The main area is a full-width user table with a leading checkbox column for row selection. Above the table, a sticky selection toolbar appears as soon as at least one row is checked; it shows the count of selected users and a prominent "Download ZIP" button. Pagination sits below the table.

**Supervisor / Mentor Report Download**

The page opens with a role info banner explaining that the download is limited to the viewer's team. The user list is pre-filtered to direct reports and mentees — no company or user filter controls are shown. The Report Type section renders identically in appearance to the admin version, but types the viewer is not permitted to access are rendered with reduced opacity, a lock icon, and a tooltip reading "Access restricted by your administrator." Only permitted report types are checkable.

**Report Access Control (Admin Only)**

This page is a vertical accordion list. Each top-level item represents a role group: Admin, Supervisor, Mentor. Expanding a group reveals a grid of report type rows. Each row has a toggle switch for global enable/disable within that role, and an optional staff-override section showing assignee chips. An "Add override" button opens a small modal with a user search field. A "Save Changes" button is anchored at the bottom of the page.

**Role-Based Conditional UI Summary**

- Admin: sees all companies, all users, all report types, all three pages.
- Supervisor / Mentor: sees "My Team Reports" only, with report types restricted to what the admin has enabled for their role.
- Locked report type indicators (lock icon + reduced opacity) appear only on the Supervisor/Mentor page.
- The bulk selection toolbar animates in when one or more rows are selected and disappears when the selection is cleared.
