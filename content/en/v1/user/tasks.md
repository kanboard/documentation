---
title: Tasks
toc: true
menu:
    main:
        parent: Using Kanboard
aliases:
    - /en/latest/user_guide/tasks.html
    - /en/1.2.24/user_guide/tasks.html
    - /en/1.2.23/user_guide/tasks.html
    - /en/1.2.22/user_guide/tasks.html
    - /en/1.2.21/user_guide/tasks.html
    - /en/1.2.20/user_guide/tasks.html
---

Creating Tasks
--------------

From the board, click on the plus sign next to the column name:

![Task creation from the board](/images/v1/task-creation-board.png)

Then the task creation form appears:

![Task Creation Form](/images/v1/task-creation-form.png)

- **Title**: The title of your task, which will be displayed on the board.
- **Description**: A description that uses Markdown syntax.
- **Tags**: The list of tags associated with tasks.
- **Create another task**: Check this box if you want to create a similar task (some fields will be pre-filled).
- **Color**: Choose the color of the card.
- **Assignee**: The person who will work on the task.
- **Category**: Only one category can be assigned to a task (visible only if the project has categories).
- **Column**: The column where the task will be created. Your task will be positioned at the bottom.
- **Priority**: Task priority. The range can be defined in the project settings. Default values are P0 to P3.
- **Complexity**: Used in agile project management (Scrum). The complexity or story points is a number that tells the team how hard the story is. Often, people use the Fibonacci series.
- **Reference**: External ID for the task. For example, it can be a ticket number from another system.
- **Original Estimate**: Estimation in hours to complete the task.
- **Time Spent**: Time spent working on the task.
- **Start Date**: This is a date-time field.
- **Due Date**: Overdue tasks will have a red due date, and upcoming due dates will be black on the board. Several date formats are accepted in addition to the date picker.

With the preview link, you can see the task description converted from Markdown syntax.

Duplicating and Moving Tasks
----------------------------

### Duplicate a task into the same project

Go to the task view and choose **Duplicate** on the left.

![Duplicate a task into the same project](/images/v1/task-duplication.png)

A new task will be created with the same properties as the original.

### Duplicate a task to another project

Go to the task view and choose **Duplicate to another project**.

![Duplicate a task to another project](/images/v1/task-duplication-another-project.png)

Only projects where you are a member will be shown in the dropdown.

Before copying the task, Kanboard will ask you to define the destination properties that are not common between the source and destination project.

You need to define:

- The destination swimlane
- The column
- The category
- The assignee

### Move a task to another project

Go to the task view and choose **Move to another project**.

Moving a task to another project works in the same way as duplication. You have to choose the new properties of the task.

### List of duplicated properties

- `title`
- `description`
- `date_due`
- `color_id`
- `project_id`
- `column_id`
- `owner_id`
- `score`
- `category_id`
- `time_estimated`
- `swimlane_id`
- `recurrence_status`
- `recurrence_trigger`
- `recurrence_factor`
- `recurrence_timeframe`
- `recurrence_basedate`

Closing Tasks
-------------

When a task is closed, it is hidden from the board.

However, you can always access the list of closed tasks by using the query **status:closed** in any search form or by choosing **Closed tasks** from the filter dropdown.

There are two ways to close a task:

- From the task dropdown menu on the board:

![Menu to close a task](/images/v1/menu-close-task.png)

- From the task sidebar menu in the task detail view:

![Closing Tasks](/images/v1/closing-tasks.png)

Note: When you close a task, all incomplete subtasks will be changed to the status "Done."

Internal Task Links
-------------------

Tasks can be linked together with predefined relationships:

![Internal Task Links](/images/v1/internal-task-links.png)

It is also possible to link tasks across projects.

The default relationships are:

- **relates to**
- **blocks** | **is blocked by**
- **duplicates** | **is duplicated by**
- **is a child of** | **is a parent of**
- **targets milestone** | **is a milestone of**
- **fixes** | **is fixed by**

These labels can be changed in the application settings.

Task Transitions
----------------

Each movement of a task between columns is recorded in the database.

![Task Transitions](/images/v1/task-transitions.png)

Available from the task view, you can see the following information:

- Date of the action
- Source column
- Destination column
- Executor (user who moved the task)
- Time spent in the origin column

Recurring Tasks
---------------

To fit with the Kanban methodology, recurring tasks are not based on a date but on board events.

- Recurring tasks are duplicated to the first column of the board when the selected events occur.
- The due date can be recalculated automatically.
- Each task records the task ID of the parent task that created it and the child task created.

### Configuration

Go to the task view page or use the dropdown menu on the board, then select **Edit recurrence**.

![Recurring Tasks](/images/v1/recurring-tasks.png)

There are three triggers that currently create a new recurring task:

- Moving a task from the first column
- Moving a task to the last column
- Closing the task

Due dates, if set on the current task, can be recalculated by a given factor of days, months, or years.
The base date for the calculation of the new due date can be either the existing due date or the action date.

Adding Screenshots
------------------

You can copy and paste images directly into Kanboard to save time. These images are uploaded as attachments to the task.

This is especially useful for taking screenshots to describe an issue, for example.

You can add screenshots directly from the board by clicking on the dropdown menu or in the task view page.

![Screenshot dropdown](/images/v1/dropdown-screenshot.png)

To add a new image, take your screenshot and paste it with `CTRL+v` or `Command+v`:

![Task Screenshot](/images/v1/task-screenshot.png)

On macOS, you can use these shortcuts to take screenshots:

- `Command-Control-Shift-3`: Take a screenshot of the screen and save it to the clipboard.
- `Command-Control-Shift-4`, then select an area: Take a screenshot of the area and save it to the clipboard.
- `Command-Control-Shift-4`, then space, then click a window: Take a screenshot of a window and save it to the clipboard.

There are also several third-party applications that can be used to take screenshots with annotations and shapes.

{{< hint type="warning" >}}
**This feature doesn't work with all browsers.** It does not work with Safari due to this bug: <https://bugs.webkit.org/show_bug.cgi?id=49141>
{{</ hint >}}

Tags
----

With Kanboard, you can associate one or many tags with a task.
You can define tags globally for all projects or only for a specific project.

![Board Tags](/images/v1/tags-board.png)

From the task form, you can enter the desired tags:

![Task Tags](/images/v1/tags-task.png)

The auto-completion form will show up to suggest available tags.

You can also create tags directly from the task form.
By default, when you create tags from a task form, they are associated with the current project:

![Project Tags](/images/v1/tags-projects.png)

All tags can be managed in the project settings.

To define tags globally for all projects, go to the application settings:

![Global Tags](/images/v1/tags-global.png)

To search tasks based on tags, just use the attribute "tag":

![Tags Search](/images/v1/tags-search.png)

Analytics
---------

Each task has an analytics section available from the left menu in the task view.

### Lead and Cycle Time

![Lead and Cycle Time](/images/v1/task-lead-cycle-time.png)

- The lead time is the time between the task creation and the date of completion (task closed).
- The cycle time is the time between the start date and the date of completion.
- If the task is not closed, the current time is used instead of the date of completion.
- If the start date is not specified, the cycle time is not calculated.

Note: You can configure an automatic action to define the start date automatically when you move a task to the column of your choice.

### Time Spent in Each Column

![Time Spent Into Each Column](/images/v1/time-into-each-column.png)

- This chart shows the total time spent in each column for the task.
- The time spent is calculated until the task is closed.
