---
sidebar_position: 3
---

# Custom Fields

Each ticket type can define a set of custom fields that are collected when creating or editing a ticket of that type. This allows you to capture type-specific information beyond the standard ticket fields.

## Schema Structure

Custom field schemas are stored as JSON in the ticket type's `schema_definition` column. The top-level structure is:

```json
{
  "fields": [
    { ... },
    { ... }
  ]
}
```

## Supported Field Types

| Type | Description |
|---|---|
| `text` | Single-line text input |
| `string` | Alias for `text` — single-line text input |
| `number` | Numeric input |
| `date` | Date picker |
| `textarea` | Multi-line text input |
| `select` | Dropdown with predefined options |

## Field Properties

Each field in the `fields` array can have the following properties:

| Property | Required | Description |
|---|---|---|
| `key` | Yes | Internal storage key; must be unique within the schema |
| `label` | Yes | Display name shown on the form |
| `type` | Yes | One of: `text`, `string`, `number`, `date`, `textarea`, `select` |
| `required` | No | `true` if the field must be filled in |
| `options` | For `select` only | Array of strings listing the available choices |

## Where Values Are Stored

Custom field values are stored in the ticket's `custom_fields` JSON column, keyed by the field's `key`. For example, a field with `key: "pio_name"` would be stored as:

```json
{
  "pio_name": "John Smith"
}
```

## Validation

Required custom fields are validated on both ticket creation and updates. Submitting a ticket without a required custom field will return a validation error.

## Example: RTI Application Schema

```json
{
  "fields": [
    {
      "key": "pio_name",
      "label": "PIO Name",
      "type": "string",
      "required": true
    },
    {
      "key": "department",
      "label": "Department",
      "type": "string",
      "required": false
    },
    {
      "key": "mode_of_filing",
      "label": "Mode of Filing",
      "type": "select",
      "required": true,
      "options": ["online_portal", "speed_post", "in_person"]
    },
    {
      "key": "first_appeal_deadline",
      "label": "First Appeal Deadline",
      "type": "date"
    }
  ]
}
```
