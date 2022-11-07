---
title: Internal Task Link API Procedures
toc: true
---

createTaskLink
--------------

- Purpose: **Create a link between two tasks**
- Parameters:
    - **task\_id** (integer, required)
    - **opposite\_task\_id** (integer, required)
    - **link\_id** (integer, required)
- Result on success: **task\_link\_id**
- Result on failure: **false**

Request example:

```json
{
    "jsonrpc": "2.0",
    "method": "createTaskLink",
    "id": 509742912,
    "params": [
        2,
        3,
        1
    ]
}
```

Response example:

```json
{
    "jsonrpc": "2.0",
    "id": 509742912,
    "result": 1
}
```

updateTaskLink
--------------

- Purpose: **Update task link**
- Parameters:
    - **task\_link\_id** (integer, required)
    - **task\_id** (integer, required)
    - **opposite\_task\_id** (integer, required)
    - **link\_id** (integer, required)
- Result on success: **true**
- Result on failure: **false**

Request example:

```json
{
    "jsonrpc": "2.0",
    "method": "updateTaskLink",
    "id": 669037109,
    "params": [
        1,
        2,
        4,
        2
    ]
}
```

Response example:

```json
{
    "jsonrpc": "2.0",
    "id": 669037109,
    "result": true
}
```

getTaskLinkById
---------------

- Purpose: **Get a task link**
- Parameters:
    - **task\_link\_id** (integer, required)
- Result on success: **task link properties**
- Result on failure: **false**

Request example:

```json
{
    "jsonrpc": "2.0",
    "method": "getTaskLinkById",
    "id": 809885202,
    "params": [
        1
    ]
}
```

Response example:

```json
{
    "jsonrpc": "2.0",
    "id": 809885202,
    "result": {
        "id": "1",
        "link_id": "1",
        "task_id": "2",
        "opposite_task_id": "3"
    }
}
```

getAllTaskLinks
---------------

- Purpose: **Get all links related to a task**
- Parameters:
    - **task\_id** (integer, required)
- Result on success: **list of task link**
- Result on failure: **false**

Request example:

```json
{
    "jsonrpc": "2.0",
    "method": "getAllTaskLinks",
    "id": 810848359,
    "params": [
        2
    ]
}
```

Response example:

```json
{
    "jsonrpc": "2.0",
    "id": 810848359,
    "result": [
        {
            "id": "1",
            "task_id": "3",
            "label": "relates to",
            "title": "B",
            "is_active": "1",
            "project_id": "1",
            "task_time_spent": "0",
            "task_time_estimated": "0",
            "task_assignee_id": "0",
            "task_assignee_username": null,
            "task_assignee_name": null,
            "column_title": "Backlog"
        }
    ]
}
```

removeTaskLink
--------------

- Purpose: **Remove a link between two tasks**
- Parameters:
    - **task\_link\_id** (integer, required)
- Result on success: **true**
- Result on failure: **false**

Request example:

```json
{
    "jsonrpc": "2.0",
    "method": "removeTaskLink",
    "id": 473028226,
    "params": [
        1
    ]
}
```

Response example:

```json
{
    "jsonrpc": "2.0",
    "id": 473028226,
    "result": true
}
```
