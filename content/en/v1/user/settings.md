---
title: Settings
toc: true
menu:
    main:
        parent: Using Kanboard
---

Some parameters for the application can be changed on the settings page.
Only administrators can change these settings.

Application Settings
--------------------

Go to the menu **Settings**, then choose **Application settings** on the left.

![Application Settings](/images/v1/application-settings.png)

### Application URL

This parameter is used for email notifications.
The email footer will contain a link to the Kanboard task.

### Language

The application language can be changed at any time.
The language will be set for all users.

### Time Zone

By default, Kanboard uses UTC as the time zone, but you can define your own time zone.
The list contains all time zones supported by your web server.

### Date Format

Input format used for date fields, such as the due date for tasks.

Kanboard offers four different formats:

- `DD/MM/YYYY`
- `MM/DD/YYYY` (default)
- `YYYY/MM/DD`
- `MM.DD.YYYY`

The [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) format is always accepted (`YYYY-MM-DD` or `YYYY_MM_DD`).

### Custom Stylesheet

Write your own CSS to override or improve Kanboard's default style.

Here is an example to change the color of category labels:

For the category container:

```css
.task-board-category-container-color span {
  border: solid 0.5px grey;
  color: black;
}
```

Custom CSS values for one category (example for displaying the text):

```css
[class*="category-MyLabel"] {
  background-color: rgba(255, 0, 0, 0.50);
  border: none!important;
  font-weight: bold;
  font-style: italic;
  box-shadow: 0 1px 1px rgba(186, 186, 186, 0.55);
  color: white!important;
  font-size: 11px;
}
```

Project Settings
----------------

Go to the menu **Settings**, then choose **Project settings** on the left.

![Project Settings](/images/v1/project-settings.png)

### Default Columns for New Projects

You can change the default column names here.
This is useful if you always create projects with the same columns.

Each column name must be separated by a comma.

By default, Kanboard uses these column names: Backlog, Ready, Work in Progress, and Done.

### Default Categories for New Projects

Categories are not global to the application but are attached to a project.
Each project can have different categories.

However, if you always create the same categories for all your projects,
you can define the list of categories to create automatically here.

### Allow Only One Subtask in Progress at the Same Time for a User

When this option is enabled, a user can work on only one subtask at a time.

If another subtask has the status "In Progress," the user will see this dialog box:

![Subtask User Restriction](/images/v1/subtask-user-restriction.png)

### Trigger Automatically Subtask Time Tracking

- If enabled, when a subtask status is changed to "In Progress," the timer will start automatically.
- Disable this option if you don't use time tracking.

### Include Closed Tasks in the Cumulative Flow Diagram

- If enabled, closed tasks will be included in the cumulative flow diagram.
- If disabled, only open tasks will be included.
- This option affects the column `total` of the table `project_daily_column_stats`.

Board Settings
--------------

Go to the menu **Settings**, then choose **Board settings** on the left.

![Board Settings](/images/v1/board-settings.png)

### Task Highlighting

This feature displays a shadow around the task when a task has been moved recently.

Set the value to 0 to disable this feature. The default is 2 days (172800 seconds).

Everything moved within the last 2 days will have a shadow around the task.

### Refresh Interval for Public Board

When you share a board, the page will refresh every 60 seconds automatically by default.

### Refresh Interval for Private Board

When your web browser is open on a board, Kanboard checks every 10 seconds if something has been changed by someone else.

Technically, this process is done by Ajax polling.

Calendar Settings
-----------------

Go to the menu **Settings**, then choose **Calendar settings** on the left.

![Calendar Settings](/images/v1/calendar-settings.png)

There are two different calendars in Kanboard:

- Project calendar
- User calendar (available from the dashboard)

### Project Calendar

This calendar shows tasks with a defined due date and tasks based on the creation date or the start date.

Show tasks based on the creation date:

- The start date of the calendar event is the creation date of the task.
- The end date of the event is the date of completion.

Show tasks based on the start date:

- The start date of the calendar event is the start date of the task.
- This date can be defined manually.
- The end date of the event is the date of completion.
- If there is no start date, the task will not appear on the calendar.

### User Calendar

This calendar shows only tasks assigned to the user and optionally subtask information.

Show subtasks based on time tracking:

- Display subtasks in the calendar from the information recorded in the time tracking table.
- The intersection with the user's timetable is also calculated.

Show subtask estimates (forecast of future work):

- Display the estimate of future work for subtasks in the status "Todo" and with a defined "estimate" value.

Link Settings
-------------

Task relations can be changed from the application settings (**Settings > Link settings**).

![Link Labels](/images/v1/link-labels.png)

Each label may have an opposite label defined. If there is no opposite, the label is considered bidirectional.

![Link Label Creation](/images/v1/link-label-creation.png)
