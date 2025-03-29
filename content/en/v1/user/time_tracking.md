---
title: Time Tracking
toc: true
menu:
    main:
        parent: Using Kanboard
---

Time tracking information can be defined at the task level or the subtask level.

Task Time Tracking
------------------

![Task Time Tracking](/images/v1/task-time-tracking.png)

Tasks have two fields:

- Time estimated
- Time spent

These values represent hours of work and must be set manually.

Subtask Time Tracking
---------------------

![Subtask Time Tracking](/images/v1/subtask-time-tracking.png)

Subtasks also have the fields "time spent" and "time estimated".

When you change the value of these fields, **the task time tracking values are updated automatically and become the sum of all subtask values**.

Kanboard records the time between each subtask status change in a separate table.

- Changing a subtask status from **todo** to **in progress** logs the start time.
- Changing a subtask status from **in progress** to **done** logs the end time and updates the time spent for both the subtask and the task.

The breakdown of all records is visible on the task view page:

![Task Timesheet](/images/v1/task-timesheet.png)

For each subtask, the timer can be stopped/started at any time:

![Subtask Timer](/images/v1/subtask-timer.png)

- The timer doesn't depend on the subtask status.
- Each time you start the timer, a new record is created in the time tracking table.
- Each time you stop the timer, the end date is recorded in the time tracking table.
- The calculated time spent is rounded to the nearest quarter (only for Kanboard < 1.0.32).
