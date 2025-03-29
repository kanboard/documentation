---
title: Advanced Search Syntax
toc: true
menu:
    main:
        parent: Using Kanboard
---

Kanboard uses a simple query language for advanced search.
You can search in tasks, comments, subtasks, links, and the activity stream.

Example of Query
----------------

This example will return all tasks assigned to me with a due date for tomorrow and a title that contains "my title":

```
assignee:me due:tomorrow my title
```

Project Search
--------------

### Search by Task ID or Title

- Search by task ID: `#123`
- Search by task ID and task title: `123`
- Search by task title: anything that doesn't match any search attributes

### Search by Status

Attribute: **status**

- Query to find open tasks: `status:open`
- Query to find closed tasks: `status:closed`

### Search by Assignee

Attribute: **assignee**

- Query with the full name: `assignee:"Frederic Guillot"`
- Query with the username: `assignee:fguillot`
- Multiple assignee lookup: `assignee:user1 assignee:"John Doe"`
- Query for unassigned tasks: `assignee:nobody`
- Query for tasks assigned to me: `assignee:me`

### Search by Task Creator

Attribute: **creator**

- Tasks created by me: `creator:me`
- Tasks created by John Doe: `creator:"John Doe"`
- Tasks created by the user ID \#1: `creator:1`

### Search by Subtask Assignee

Attribute: **subtask:assignee**

- Example: `subtask:assignee:"John Doe"`

### Search by Color

Attribute: **color**

- Query to search by color ID: `color:blue`
- Query to search by color name: `color:"Deep Orange"`

### Search by Due Date

Attribute: **due**

- Search tasks due today: `due:today`
- Search tasks due tomorrow: `due:tomorrow`
- Search tasks due yesterday: `due:yesterday`
- Search tasks due on an exact date: `due:2015-06-29`
- Search tasks without a due date: `due:none`

The date must use the ISO 8601 format: **YYYY-MM-DD**.

All string formats supported by the [strtotime() function](https://www.php.net/strtotime) are supported, for example `next Thursday`, `-2 days`, `+2 months`, `tomorrow`, etc.
If there are spaces, they must be enclosed in double quotes.

Operators supported with a date:

- Greater than: **due:>2015-06-29**
- Less than: **due:<2015-06-29**
- Greater than or equal: **due:>=2015-06-29**
- Less than or equal: **due:<=2015-06-29**

### Search by Modification Date

Attribute: **modified** or **updated**

The date formats are the same as those for the due date.

There is also a filter for recently modified tasks: `modified:recently`.

This query uses the same value as the board highlight period configured in settings.

### Search by Creation Date

Attribute: **created**

Works in the same way as modification date queries.

### Search by Creation Date with Range

Attribute: **createdRange**

- Date separator: `..` (two dots)
- Example: `createdRange:2018/01/21..2018/01/31` or `createdRange:"2018-01-21..2018-01-31"`

### Search by Completion Date with Range

Attribute: **completedRange**

- Date separator: `..` (two dots)
- Example: `completedRange:2018/01/21..2018/01/31` or `completedRange:"2018-01-21..2018-01-31"`

### Search by Modification Date with Range

Attribute: **updatedRange**, **modifiedRange**

- Date separator: `..` (two dots)
- Example: `updatedRange:2018/01/21..2018/01/31` or `updatedRange:"2018-01-21..2018-01-31"`

### Search by Moved Date with Range

Attribute: **movedRange**

- Date separator: `..` (two dots)
- Example: `movedRange:2018/01/21..2018/01/31` or `movedRange:"2018-01-21..2018-01-31"`

### Search by Start Date

Attribute: **started**

### Search by Description

Attribute: **description** or **desc**

- Example: `description:"text search"`

### Search by Completion

Attribute: **completed**

### Search by External Reference

The task reference is an external ID of your task, for example, a ticket number from another software.

- Find tasks with a reference: `ref:1234` or `reference:TICKET-1234`
- Find tasks with no reference: `reference:none`
- Wildcard search: `ref:TICKET-*`

### Search by Category

Attribute: **category**

- Find tasks with a specific category: `category:"Feature Request"`
- Find all tasks that have those categories: `category:"Bug" category:"Improvements"`
- Find tasks with no category assigned: `category:none`
- Find tasks by the category ID or category name: `category:1234`

### Search by Project

Attribute: **project**

- Find tasks by project name: `project:"My project name"`
- Find tasks by project ID: `project:23`
- Find tasks for several projects: `project:"My project A" project:"My project B"`

### Search by Columns

Attribute: **column**

- Find tasks by column name: `column:"Work in progress"`
- Find tasks for several columns: `column:"Backlog" column:ready`

### Search by Swimlane

Attribute: **swimlane**

- Find tasks by swimlane: `swimlane:"Version 42"`
- Find tasks in several swimlanes: `swimlane:"Version 1.2" swimlane:"Version 1.3"`

### Search by Task Link

Attribute: **link**

- Find tasks by link name: `link:"is a milestone of"`
- Find tasks in several links: `link:"is a milestone of" link:"relates to"`

### Search by Comment

Attribute: **comment**

- Find comments that contain this text: `comment:"My comment message"`

### Search by Tags

Attribute: **tag**

- Example: `tag:"My tag"`

### Search by Score/Complexity

Attribute: **score** or **complexity**

- Example: `score:>=21`
- Example: `complexity:8`

Activity Stream Search
----------------------

### Search Events by Task Title

Attribute: **title** or none (default)

- Example: `title:"My task"`
- Search by task ID: `#123`

### Search Events by Task Status

Attribute: **status**

### Search by Event Creator

Attribute: **creator**

### Search by Event Creation Date

Attribute: **created**

### Search Events by Project

Attribute: **project**
