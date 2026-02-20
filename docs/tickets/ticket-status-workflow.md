---
sidebar_position: 5
---

# Ticket Status Workflow

Tickets move through a defined set of statuses. Not every transition is allowed — the system enforces a state machine to ensure a logical progression.

## Statuses

| Value | Label | Description |
|---|---|---|
| `draft` | **Draft** | Ticket has been created but not yet submitted |
| `submitted` | **Submitted** | Ticket has been filed and is awaiting acknowledgement |
| `acknowledged` | **Acknowledged** | Receipt of the complaint has been confirmed |
| `in_progress` | **In Progress** | Actively being worked on |
| `escalated` | **Escalated** | Raised to a higher authority or priority level |
| `resolved` | **Resolved** | The issue has been addressed; awaiting final closure |
| `closed` | **Closed** | Ticket is complete; `closed_date` is recorded automatically |
| `reopened` | **Reopened** | A previously closed ticket has been re-opened |

## Allowed Transitions

| Current Status | Can Move To |
|---|---|
| Draft | Submitted |
| Submitted | Acknowledged, In Progress, Closed |
| Acknowledged | In Progress, Closed |
| In Progress | Resolved, Escalated, Closed |
| Escalated | Resolved, Closed |
| Resolved | Closed |
| Closed | Reopened |
| Reopened | In Progress, Closed |

## Notes

- **Closing** a ticket automatically records the current date and time as the `closed_date`.
- Attempting an invalid transition returns a validation error; the ticket remains in its current state.
- The **Change Status** dropdown on the ticket detail page only shows valid transitions, preventing invalid moves in the UI.
