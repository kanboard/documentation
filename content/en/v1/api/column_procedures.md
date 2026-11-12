---
title: Column API Procedures
toc: true
menu:
    main:
        parent: API Reference
---

getColumns
----------

- Purpose: **Get all columns information for a given project**
- Parameters:
    - **project_id** (integer, required)
- Result on success: **columns properties**
- Result on failure: **empty list**

Request example:

```json
{
    "jsonrpc": "2.0",
    "method": "getColumns",
    "id": 887036325,
    "params": [
        1
    ]
}
```

Response example (Kanboard 1.2.54, PostgreSQL 17, PHP 8.4):

```json
{
    "jsonrpc": "2.0",
    "id": 887036325,
    "result": [
        {
            "id": 1,
            "title": "Backlog",
            "position": 1,
            "project_id": 1,
            "task_limit": 0,
            "description": "",
            "hide_in_dashboard": false
        },
        {
            "id": 2,
            "title": "Ready",
            "position": 2,
            "project_id": 1,
            "task_limit": 0,
            "description": "",
            "hide_in_dashboard": false
        },
        {
            "id": 3,
            "title": "Work in progress",
            "position": 3,
            "project_id": 1,
            "task_limit": 0,
            "description": "",
            "hide_in_dashboard": false
        },
        {
            "id": 4,
            "title": "Done",
            "position": 4,
            "project_id": 1,
            "task_limit": 0,
            "description": "",
            "hide_in_dashboard": false
        }
    ]
}
```

getColumn
---------

- Purpose: **Get a single column**
- Parameters:
    - **column_id** (integer, required)
- Result on success: **column properties**
- Result on failure: **null**

Request example:

```json
{
    "jsonrpc": "2.0",
    "method": "getColumn",
    "id": 1242049935,
    "params": [
        1
    ]
}
```

Response example (Kanboard 1.2.54, PostgreSQL 17, PHP 8.4):

```json
{
    "jsonrpc": "2.0",
    "id": 1242049935,
    "result": {
        "id": 1,
        "title": "Backlog",
        "position": 1,
        "project_id": 1,
        "task_limit": 0,
        "description": "",
        "hide_in_dashboard": false
    }
}
```

changeColumnPosition
--------------------

- Purpose: **Change the column position**
- Parameters:
    - **project_id** (integer, required)
    - **column_id** (integer, required)
    - **position** (integer, required, must be >= 1)
- Result on success: **true**
- Result on failure: **false**

Request example:

```json
{
    "jsonrpc": "2.0",
    "method": "changeColumnPosition",
    "id": 99275573,
    "params": [
        1,
        2,
        3
    ]
}
```

Response example:

```json
{
    "jsonrpc": "2.0",
    "id": 99275573,
    "result": true
}
```

updateColumn
------------

- Purpose: **Update column properties**
- Parameters:
    - **column_id** (integer, required)
    - **title** (string, required)
    - **task_limit** (integer, optional)
    - **description** (string, optional)
- Result on success: **true**
- Result on failure: **false**

Request example:

```json
{
    "jsonrpc": "2.0",
    "method": "updateColumn",
    "id": 480740641,
    "params": [
        2,
        "Boo",
        5
    ]
}
```

Response example:

```json
{
    "jsonrpc": "2.0",
    "id": 480740641,
    "result": true
}
```

addColumn
---------

- Purpose: **Add a new column**
- Parameters:
    - **project_id** (integer, required)
    - **title** (string, required)
    - **task_limit** (integer, optional)
    - **description** (string, optional)
- Result on success: **column_id**
- Result on failure: **false**

Request example:

```json
{
    "jsonrpc": "2.0",
    "method": "addColumn",
    "id": 638544704,
    "params": [
        1,
        "Boo"
    ]
}
```

Response example:

```json
{
    "jsonrpc": "2.0",
    "id": 638544704,
    "result": 5
}
```

removeColumn
------------

- Purpose: **Remove a column**
- Parameters:
    - **column_id** (integer, required)
- Result on success: **true**
- Result on failure: **false**

Request example:

```json
{
    "jsonrpc": "2.0",
    "method": "removeColumn",
    "id": 1433237746,
    "params": [
        1
    ]
}
```

Response example:

```json
{
    "jsonrpc": "2.0",
    "id": 1433237746,
    "result": true
}
```
