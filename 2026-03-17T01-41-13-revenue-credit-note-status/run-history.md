## User Prompt

Here is how revenue credit note status block looks like.

![%D0%B8%D0%B7%D0%BE%D0%B1%D1%80%D0%B0%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5.webp](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T01-41-13-revenue-credit-note-status/01-user-prompt-image-01.png)

We would like to change it so that it will follow provision status UX.

![%D0%B8%D0%B7%D0%BE%D0%B1%D1%80%D0%B0%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5.webp](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T01-41-13-revenue-credit-note-status/01-user-prompt-image-02.png)

1. Rollback changes credit note status from approved to draft
2. Cancel cancels credit note

---

## UI Research

### Module
Revenue Credit Notes Status Block — Amendment to display provision UX pattern with rollback and cancel capabilities

### Reference Page
- **Path:** `UFGPM.Web.UI/src/pages/invoice/containers/InvoicePage.tsx`
- **Layout:** Modal with EntityModal wrapper and status display via AdminModalTitle component
- **Components used:** AdminModalTitle, EntityModal, Label, StatusLine, ConfirmButton, Button
- **Patterns noted:**
  - Status badges displayed in modal header via AdminModalTitle component
  - Read-only badge displayed when entity cannot be edited
  - Status field uses InvoiceStatusField widget which renders a StatusLine component
  - Action buttons are grouped using flexbox (d-flex) with gap utilities
  - Buttons use variant props for styling (success, warning, danger)
  - ConfirmButton wraps destructive actions with confirmation text

### Similar Patterns

- Provision status UX pattern — Shows StatusLine with Draft/Provision states and action buttons (Provision, Rollback, Cancel) — `UFGPM.Web.UI/src/pages/invoice/components/InvoiceStatusField.tsx` (lines 215–279)
  - Buttons for forward progression: "Approve", "Allocate"
  - Button for rollback: "Roll back" (warning variant)
  - Button for cancellation: "Cancel" (danger variant)
  - Conditional rendering based on current status and canWrite/canRollback flags
- StatusLine component — Renders visual status progression with circular indicators and connecting lines — `UFGPM.Web.UI/src/components/StatusLine/StatusLine.tsx`
- Label/Badge component — Renders colored status badges with light/dark variants — `UFGPM.Web.UI/src/components/Labels/Label.tsx`

### Components Needed
- **StatusLine** — `UFGPM.Web.UI/src/components/StatusLine/StatusLine.tsx`
- **Label** — `UFGPM.Web.UI/src/components/Labels/Label.tsx`
- **ConfirmButton** — `UFGPM.Web.UI/src/components/Button/ConfirmButton.tsx`
- **Button** — `UFGPM.Web.UI/src/components/Button`

### Image Observations
- Image 1: Single "APPROVED" status badge (red/pink color) positioned at top-right of modal header; compact pill-shaped element
- Image 2: Two status badges side-by-side — "APPROVED" (yellow/gold) and "CANCELLED" (red/pink) at top-right of modal header
- Both images show badges as inline elements within the modal title/header area
- Status badges use Label component with different color variants (danger for approved/cancelled states)
- Layout supports multiple badges displayed together in the header

---

## Revision 1

This design update replaces the simple status badge on the Revenue Credit Note modal with a richer, provision-style status block — matching the UX pattern already used for standard invoices. The status block combines a horizontal progress bar (showing each stage as a circle connected by a line) with contextual action buttons directly beneath it. The change affects two visible states of the credit note: Approved (where workflow actions are still available) and Cancelled (a terminal, read-only state).

The key behavioural changes are:

- **Roll back** — previously unavailable on credit notes, this new amber button lets an authorised user demote the credit note from Approved back to Draft. It triggers a confirmation prompt before executing.
- **Cancel** — previously present only as a destructive badge action, this red button now sits alongside Roll back in a consistent button row beneath the status line. It also requires confirmation before proceeding.
- When a credit note reaches the **Cancelled** state, both buttons disappear and the form becomes fully read-only. A terminal "Cancelled" label is displayed alongside the completed status line, making it immediately clear that no further actions are possible.

![View 1 — Credit Note in Approved State](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T01-41-13-revenue-credit-note-status/03-r1-mockup-credit-note-approved.png)
[Open mockup](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T01-41-13-revenue-credit-note-status/03-r1-mockup-credit-note-approved.html)

![View 2 — Credit Note in Cancelled State](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T01-41-13-revenue-credit-note-status/03-r1-mockup-credit-note-cancelled.png)
[Open mockup](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T01-41-13-revenue-credit-note-status/03-r1-mockup-credit-note-cancelled.html)

## Layout Notes

- The status block sits inside a lightly bordered, padded panel that spans the full width of the form area — the same visual container used by the provision status field on standard invoices.
- The progress bar circles are sized at 25 px, connected by a thin horizontal rule that fills/dims to indicate completion state.
- The "Cancelled" terminal state is not a regular step in the progress line; it is a distinct red badge that appears to the right of the last completed step, visually separated to signal it is an out-of-band termination rather than a normal workflow progression.
- Action buttons are small (sm size), centred horizontally, and use consistent icon glyphs: an undo arrow for Roll back, an × for Cancel.
- The modal is rendered at 80 % viewport width on a 1600 px canvas, matching the existing credit note modal configuration.
