---
sidebar_position: 1
---

# Managing Reminders

Reminders alert you to upcoming deadlines and follow-up actions. They are managed from the **Reminders** tab on each ticket's detail page.

## Automatic Deadline Reminders

When a **due date** is set on a ticket, Open Docket automatically creates three reminders:

| Trigger | Time |
|---|---|
| 3 days before due date | 09:00 |
| 1 day before due date | 09:00 |
| On the due date | 09:00 |

If the calculated reminder time is already in the past, that reminder is skipped and not created.

## Manual Reminders

You can add your own reminders from the Reminders tab. Click **Add Reminder** and fill in the form:

| Field | Notes |
|---|---|
| **Title** | Required. A short description of what to do. |
| **Remind At** | Required. The date and time for the reminder. |
| **Type** | Choose: **Deadline Approaching**, **Follow-Up**, or **Custom** |
| **Notes** | Optional. Additional context. |

## Recurring Reminders

Toggle **Recurring** on to make the reminder repeat. When enabled, additional options appear:

| Option | Description |
|---|---|
| **Pattern** | Every 7 days / Every 30 days / Every weekday |
| **End Date** | Optional date to stop generating new occurrences |

## Reminder Status Badges

| Badge | Meaning |
|---|---|
| **Sent** | The reminder has been dispatched by the background scheduler |
| **Overdue** | The reminder time has passed and it has not been sent |

## Dashboard Widget

The [Dashboard](../getting-started/dashboard.md) shows the next 7 days of **unsent** reminders across all tickets.
