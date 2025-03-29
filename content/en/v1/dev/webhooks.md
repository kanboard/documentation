---
title: Webhooks
toc: true
menu:
    main:
        parent: Contributing to Kanboard
---

Webhooks allow you to perform actions with external applications.

- Webhooks can create a task by calling a simple URL (this can also be done with the API).
- An external URL can be called automatically when an event occurs in Kanboard (e.g., task creation, comment update).

## How to Write a Webhook Receiver

All internal events of Kanboard can be sent to an external URL.

- Define the webhook URL in **Settings > Webhooks > Webhook URL**.
- When an event is triggered, Kanboard automatically calls the pre-defined URL.
- Data is encoded in JSON format and sent via a POST HTTP request.
- The webhook token is sent as a query string parameter, allowing you to verify the request's origin.
- **Your custom URL must respond in less than 1 second.** These requests are synchronous (due to PHP limitations) and can slow down the user interface if your script is too slow.

### List of Supported Events

- `comment.create`
- `comment.update`
- `comment.delete`
- `file.create`
- `task.move.project`
- `task.move.column`
- `task.move.position`
- `task.move.swimlane`
- `task.update`
- `task.create`
- `task.close`
- `task.open`
- `task.assignee_change`
- `subtask.update`
- `subtask.create`
- `subtask.delete`
- `task_internal_link.create_update`
- `task_internal_link.delete`

### Example of HTTP Request

```
POST https://your_webhook_url/?token=WEBHOOK_TOKEN_HERE
User-Agent: Kanboard Webhook
Content-Type: application/json
Connection: close

{
    "event_name": "task.move.column",
    "event_data": {
        "task_id": "4",
        "task": {
            "id": "4",
            "reference": "",
            "title": "My task",
            "description": "",
            "date_creation": "1469314356",
            "date_completed": null,
            "date_modification": "1469315422",
            "date_due": "1469491200",
            "date_started": "0",
            "time_estimated": "0",
            "time_spent": "0",
            "color_id": "green",
            "project_id": "1",
            "column_id": "1",
            "owner_id": "1",
            "creator_id": "1",
            "position": "1",
            "is_active": "1",
            "score": "0",
            "category_id": "0",
            "priority": "0",
            "swimlane_id": "0",
            "date_moved": "1469315422",
            "recurrence_status": "0",
            "recurrence_trigger": "0",
            "recurrence_factor": "0",
            "recurrence_timeframe": "0",
            "recurrence_basedate": "0",
            "recurrence_parent": null,
            "recurrence_child": null,
            "category_name": null,
            "swimlane_name": null,
            "project_name": "Demo Project",
            "default_swimlane": "Default swimlane",
            "column_title": "Backlog",
            "assignee_username": "admin",
            "assignee_name": null,
            "creator_username": "admin",
            "creator_name": null
        },
        "changes": {
            "src_column_id": "2",
            "dst_column_id": "1",
            "date_moved": "1469315398"
        },
        "project_id": "1",
        "position": 1,
        "column_id": "1",
        "swimlane_id": "0",
        "src_column_id": "2",
        "dst_column_id": "1",
        "date_moved": "1469315398",
        "recurrence_status": "0",
        "recurrence_trigger": "0"
    }
}
```

All event payloads follow this format:

```json
{
  "event_name": "model.event_name",
  "event_data": {
    "key1": "value1",
    "key2": "value2"
  }
}
```

The `event_data` values are not necessarily normalized across events.

### Examples of Event Payloads

#### Task Creation

```json
{
    "event_name": "task.create",
    "event_data": {
        "task_id": 5,
        "task": {
            "id": "5",
            "reference": "",
            "title": "My new task",
            "description": "",
            "date_creation": "1469315481",
            "date_completed": null,
            "date_modification": "1469315481",
            "date_due": "0",
            "date_started": "0",
            "time_estimated": "0",
            "time_spent": "0",
            "color_id": "orange",
            "project_id": "1",
            "column_id": "2",
            "owner_id": "1",
            "creator_id": "1",
            "position": "1",
            "is_active": "1",
            "score": "3",
            "category_id": "0",
            "priority": "2",
            "swimlane_id": "0",
            "date_moved": "1469315481",
            "recurrence_status": "0",
            "recurrence_trigger": "0",
            "recurrence_factor": "0",
            "recurrence_timeframe": "0",
            "recurrence_basedate": "0",
            "recurrence_parent": null,
            "recurrence_child": null,
            "category_name": null,
            "swimlane_name": null,
            "project_name": "Demo Project",
            "default_swimlane": "Default swimlane",
            "column_title": "Ready",
            "assignee_username": "admin",
            "assignee_name": null,
            "creator_username": "admin",
            "creator_name": null
        }
    }
}
```

#### Task Modification

```json
{
    "event_name": "task.update",
    "event_data": {
        "task_id": "5",
        "task": {
            "id": "5",
            "reference": "",
            "title": "My new task",
            "description": "New description",
            "date_creation": "1469315481",
            "date_completed": null,
            "date_modification": "1469315531",
            "date_due": "1469836800",
            "date_started": "0",
            "time_estimated": "0",
            "time_spent": "0",
            "color_id": "purple",
            "project_id": "1",
            "column_id": "2",
            "owner_id": "1",
            "creator_id": "1",
            "position": "1",
            "is_active": "1",
            "score": "3",
            "category_id": "0",
            "priority": "2",
            "swimlane_id": "0",
            "date_moved": "1469315481",
            "recurrence_status": "0",
            "recurrence_trigger": "0",
            "recurrence_factor": "0",
            "recurrence_timeframe": "0",
            "recurrence_basedate": "0",
            "recurrence_parent": null,
            "recurrence_child": null,
            "category_name": null,
            "swimlane_name": null,
            "project_name": "Demo Project",
            "default_swimlane": "Default swimlane",
            "column_title": "Ready",
            "assignee_username": "admin",
            "assignee_name": null,
            "creator_username": "admin",
            "creator_name": null
        },
        "changes": {
            "description": "New description",
            "color_id": "purple",
            "date_due": 1469836800
        }
    }
}
```

#### Comment Creation

```json
{
    "event_name": "comment.create",
    "event_data": {
        "comment": {
            "id": "1",
            "task_id": "5",
            "user_id": "1",
            "date_creation": "1469315727",
            "comment": "My comment.",
            "reference": null,
            "username": "admin",
            "name": null,
            "email": null,
            "avatar_path": null
        },
        "task": {
            "id": "5",
            "reference": "",
            "title": "My new task",
            "description": "New description",
            "date_creation": "1469315481",
            "date_completed": null,
            "date_modification": "1469315531",
            "date_due": "1469836800",
            "date_started": "0",
            "time_estimated": "0",
            "time_spent": "0",
            "color_id": "purple",
            "project_id": "1",
            "column_id": "2",
            "owner_id": "1",
            "creator_id": "1",
            "position": "1",
            "is_active": "1",
            "score": "3",
            "category_id": "0",
            "priority": "2",
            "swimlane_id": "0",
            "date_moved": "1469315481",
            "recurrence_status": "0",
            "recurrence_trigger": "0",
            "recurrence_factor": "0",
            "recurrence_timeframe": "0",
            "recurrence_basedate": "0",
            "recurrence_parent": null,
            "recurrence_child": null,
            "category_name": null,
            "swimlane_name": null,
            "project_name": "Demo Project",
            "default_swimlane": "Default swimlane",
            "column_title": "Ready",
            "assignee_username": "admin",
            "assignee_name": null,
            "creator_username": "admin",
            "creator_name": null
        }
    }
}
```

#### Subtask Creation

```json
{
    "event_name": "subtask.create",
    "event_data": {
        "subtask": {
            "id": "1",
            "title": "My subtask",
            "status": "0",
            "time_estimated": "0",
            "time_spent": "0",
            "task_id": "5",
            "user_id": "1",
            "position": "1",
            "username": "admin",
            "name": null,
            "timer_start_date": 0,
            "status_name": "Todo",
            "is_timer_started": false
        },
        "task": {
            "id": "5",
            "reference": "",
            "title": "My new task",
            "description": "New description",
            "date_creation": "1469315481",
            "date_completed": null,
            "date_modification": "1469315531",
            "date_due": "1469836800",
            "date_started": "0",
            "time_estimated": "0",
            "time_spent": "0",
            "color_id": "purple",
            "project_id": "1",
            "column_id": "2",
            "owner_id": "1",
            "creator_id": "1",
            "position": "1",
            "is_active": "1",
            "score": "3",
            "category_id": "0",
            "priority": "2",
            "swimlane_id": "0",
            "date_moved": "1469315481",
            "recurrence_status": "0",
            "recurrence_trigger": "0",
            "recurrence_factor": "0",
            "recurrence_timeframe": "0",
            "recurrence_basedate": "0",
            "recurrence_parent": null,
            "recurrence_child": null,
            "category_name": null,
            "swimlane_name": null,
            "project_name": "Demo Project",
            "default_swimlane": "Default swimlane",
            "column_title": "Ready",
            "assignee_username": "admin",
            "assignee_name": null,
            "creator_username": "admin",
            "creator_name": null
        }
    }
}
```

#### File Upload

```json
{
    "event_name": "task.file.create",
    "event_data": {
        "file": {
            "id": "1",
            "name": "kanboard-latest.zip",
            "path": "tasks/5/6f32893e467e76671965b1ec58c06a2440823752",
            "is_image": "0",
            "task_id": "5",
            "date": "1469315613",
            "user_id": "1",
            "size": "4907308"
        },
        "task": {
            "id": "5",
            "reference": "",
            "title": "My new task",
            "description": "New description",
            "date_creation": "1469315481",
            "date_completed": null,
            "date_modification": "1469315531",
            "date_due": "1469836800",
            "date_started": "0",
            "time_estimated": "0",
            "time_spent": "0",
            "color_id": "purple",
            "project_id": "1",
            "column_id": "2",
            "owner_id": "1",
            "creator_id": "1",
            "position": "1",
            "is_active": "1",
            "score": "3",
            "category_id": "0",
            "priority": "2",
            "swimlane_id": "0",
            "date_moved": "1469315481",
            "recurrence_status": "0",
            "recurrence_trigger": "0",
            "recurrence_factor": "0",
            "recurrence_timeframe": "0",
            "recurrence_basedate": "0",
            "recurrence_parent": null,
            "recurrence_child": null,
            "category_name": null,
            "swimlane_name": null,
            "project_name": "Demo Project",
            "default_swimlane": "Default swimlane",
            "column_title": "Ready",
            "assignee_username": "admin",
            "assignee_name": null,
            "creator_username": "admin",
            "creator_name": null
        }
    }
}
```

#### Task Link Creation

```json
{
    "event_name": "task_internal_link.create_update",
    "event_data": {
        "task_link": {
            "id": "2",
            "opposite_task_id": "5",
            "task_id": "4",
            "link_id": "3",
            "label": "is blocked by",
            "opposite_link_id": "2"
        },
        "task": {
            "id": "4",
            "reference": "",
            "title": "My task",
            "description": "",
            "date_creation": "1469314356",
            "date_completed": null,
            "date_modification": "1469315422",
            "date_due": "1469491200",
            "date_started": "0",
            "time_estimated": "0",
            "time_spent": "0",
            "color_id": "green",
            "project_id": "1",
            "column_id": "1",
            "owner_id": "1",
            "creator_id": "1",
            "position": "1",
            "is_active": "1",
            "score": "0",
            "category_id": "0",
            "priority": "0",
            "swimlane_id": "0",
            "date_moved": "1469315422",
            "recurrence_status": "0",
            "recurrence_trigger": "0",
            "recurrence_factor": "0",
            "recurrence_timeframe": "0",
            "recurrence_basedate": "0",
            "recurrence_parent": null,
            "recurrence_child": null,
            "category_name": null,
            "swimlane_name": null,
            "project_name": "Demo Project",
            "default_swimlane": "Default swimlane",
            "column_title": "Backlog",
            "assignee_username": "admin",
            "assignee_name": null,
            "creator_username": "admin",
            "creator_name": null
        }
    }
}
```
