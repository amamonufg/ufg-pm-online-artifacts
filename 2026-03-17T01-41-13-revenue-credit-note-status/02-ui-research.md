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
