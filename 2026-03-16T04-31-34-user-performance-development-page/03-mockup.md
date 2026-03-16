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

A new set of pages for downloading performance development reports, with role-based access control. Admins can download all report types for any user in the system, with bulk ZIP download filtered by company. Supervisors and mentors see only their subordinates and mentees, and the report types available to them can be restricted through an access control configuration page.

**Views:**
- ![Admin Download Page](https://trello.com/1/cards/69b78772e1aa5c4a1aa3d0a0/attachments/69b788c5a3e7e379286ce103/download/mockup-admin-download.png)
- ![Supervisor / Mentor Download Page](https://trello.com/1/cards/69b78772e1aa5c4a1aa3d0a0/attachments/69b788ca0460863553a0a0cc/download/mockup-supervisor.png)
- ![Report Access Control Page](https://trello.com/1/cards/69b78772e1aa5c4a1aa3d0a0/attachments/69b788cf9561b0fc7d11aa7b/download/mockup-access-control.png)

### Layout Notes

- Entry point: a new "Download Reports" section in the Performance Development navigation, visible to admins, supervisors, and mentors — each sees the appropriate scoped view
- Report type columns (Annual Targets, Self Assessment, Feedback, Competency Evaluation) can be toggled in the filter bar to control what is included in downloads
- "Download selected as ZIP" becomes active once at least one user row is checked; it packages all enabled report types for all checked users into a single archive
- Individual per-row download buttons allow downloading reports for a single user without needing bulk selection
- On the Supervisor / Mentor page the user list is automatically scoped to the viewer's subordinates and mentees — no company filter is shown
- Report type columns restricted for the viewer's role are hidden entirely, so supervisors and mentors never see report types they are not permitted to access
- The Access Control page is accessible to admins only via the "Configure access" link in the page toolbar
- Access control is configured per role (Supervisor, Mentor) and per report type — changes apply to all users in that role immediately
