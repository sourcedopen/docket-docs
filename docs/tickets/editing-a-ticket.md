---
sidebar_position: 4
---

# Editing a Ticket

## Opening the Edit Form

From a ticket's detail page, click **Edit** in the actions bar. The edit form mirrors the [create form](creating-a-ticket.md) and all fields are editable.

## Quick Status Change

You do not need to open the edit form to change a ticket's status. Use the **Change Status** dropdown in the actions bar on the ticket detail page. Only valid transitions for the current status are shown.

See [Ticket Status Workflow](ticket-status-workflow.md) for the full list of allowed transitions.

## Closing a Ticket

When a ticket is moved to **Closed** status (either via the edit form or the quick status dropdown), the `closed_date` is automatically recorded to the current date and time.

## State Machine Enforcement

If you attempt an invalid status transition, a validation error is returned and the ticket remains in its current state. The "Change Status" dropdown only shows valid options, so invalid transitions are prevented in the UI.
