## Overview

This design update replaces the simple status badge on the Revenue Credit Note modal with a richer, provision-style status block — matching the UX pattern already used for standard invoices. The status block combines a horizontal progress bar (showing each stage as a circle connected by a line) with contextual action buttons directly beneath it. The change affects two visible states of the credit note: Approved (where workflow actions are still available) and Cancelled (a terminal, read-only state).

The key behavioural changes are:

- **Roll back** — previously unavailable on credit notes, this new amber button lets an authorised user demote the credit note from Approved back to Draft. It triggers a confirmation prompt before executing.
- **Cancel** — previously present only as a destructive badge action, this red button now sits alongside Roll back in a consistent button row beneath the status line. It also requires confirmation before proceeding.
- When a credit note reaches the **Cancelled** state, both buttons disappear and the form becomes fully read-only. A terminal "Cancelled" label is displayed alongside the completed status line, making it immediately clear that no further actions are possible.

### Views

**View 1 — Credit Note in Approved State (with action buttons)**
![View 1 — Credit Note in Approved State](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T01-41-13-revenue-credit-note-status/03-r1-mockup-credit-note-approved.png)
[Open mockup](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T01-41-13-revenue-credit-note-status/03-r1-mockup-credit-note-approved.html)

The modal header shows the credit note number. Below the header the Status block appears inside a bordered panel: a two-step progress bar (Draft → Approved, with Approved as the filled active circle) followed immediately by a row of two buttons — "Roll back" in amber and "Cancel" in red. The rest of the modal contains the credit note form fields in editable state.

**View 2 — Credit Note in Cancelled State (read-only)**
![View 2 — Credit Note in Cancelled State](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T01-41-13-revenue-credit-note-status/03-r1-mockup-credit-note-cancelled.png)
[Open mockup](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T01-41-13-revenue-credit-note-status/03-r1-mockup-credit-note-cancelled.html)

The same modal layout, but the status block shows all prior steps (Draft, Approved) in a completed/filled style, with a "Cancelled" terminal badge appended at the right end of the progress bar. No action buttons are rendered. All form fields appear with a muted, read-only appearance to reinforce that the record is closed.

## Layout Notes

- The status block sits inside a lightly bordered, padded panel that spans the full width of the form area — the same visual container used by the provision status field on standard invoices.
- The progress bar circles are sized at 25 px, connected by a thin horizontal rule that fills/dims to indicate completion state.
- The "Cancelled" terminal state is not a regular step in the progress line; it is a distinct red badge that appears to the right of the last completed step, visually separated to signal it is an out-of-band termination rather than a normal workflow progression.
- Action buttons are small (sm size), centred horizontally, and use consistent icon glyphs: an undo arrow for Roll back, an × for Cancel.
- The modal is rendered at 80 % viewport width on a 1600 px canvas, matching the existing credit note modal configuration.
