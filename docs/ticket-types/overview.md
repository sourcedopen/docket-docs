---
sidebar_position: 1
---

# Ticket Types Overview

**Ticket types** categorise tickets and define their default behaviour: how long resolution should take (SLA), what custom fields are collected, and how the type is visually identified.

## Type Properties

| Property | Description |
|---|---|
| **Name** | Display name shown in the UI |
| **Slug** | URL-safe identifier (auto-generated from name) |
| **Description** | Optional explanation of when to use this type |
| **Default SLA Days** | Number of days after the filed date before the ticket is considered overdue |
| **Icon** | An icon identifier for visual identification |
| **Color** | Hex color for the type badge |
| **Sort Order** | Controls display order in the type selector |
| **Active** | Only active types appear in the New Ticket type selector |

## Built-In Seed Types

Open Docket ships with the following pre-configured ticket types:

| Type | Default SLA |
|---|---|
| RTI Application | 30 days |
| DND Complaint | 7 days |
| Consumer Complaint | 45 days |
| Banking Ombudsman | 30 days |
| Insurance Complaint | 15 days |
| General Complaint | — |

These can be edited or deactivated. New types can be added at any time.

## Custom Fields

Each ticket type can define a custom field schema — additional fields collected when creating a ticket of that type. See [Custom Fields](custom-fields.md).
