Tasks
=====

Creating Tasks
--------------

From the board, click on the plus sign next to the column name:

.. figure:: /_static/task-creation-board.png
   :alt: Task creation from the board

Then the task creation form appears:

.. figure:: /_static/task-creation-form.png
   :alt: Task creation form

-  **Title**: The title of your task, which will be displayed on the
   board.
-  **Description**: Description that use the Markdown syntax.
-  **Tags**: The list of tags associated to tasks.
-  **Create another task**: Check this box if you want to create a
   similar task (some fields will be pre-filled).
-  **Color**: Choose the color of the card.
-  **Assignee**: The person that will work on the task.
-  **Category**: Only one category can be assigned to a task (visible
   only if the projects have categories).
-  **Column**: The column where the task will be created, your task will
   be positioned at the bottom.
-  **Priority**: Task priority, the range can be defined in the project
   settings, default values are P0 to P3.
-  **Complexity**: Used in agile project management (Scrum), the
   complexity or story points is a number that tells the team how hard
   the story is. Often, people use the Fibonacci series.
-  **Reference**: External ID for the task, for example it can be ticket
   number that come from another system
-  **Original Estimate**: Estimation in hours to complete the task.
-  **Time Spent**: Time spent working on the task.
-  **Start Date**: This is a date time field.
-  **Due Date**: Overdue tasks will have a red due date and upcoming due
   dates will be black on the board. Several date format are accepted in
   addition to the date picker.

With the preview link, you can see the task description converted from
the Markdown syntax.

Duplicating and Moving Tasks
----------------------------

Duplicate a task into the same project
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Go to the task view and choose **Duplicate** on the left.

.. figure:: /_static/task-duplication.png
   :alt: Task Duplication

A new task will be created with the same properties as the original.

Duplicate a task to another project
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Go to the task view and choose **Duplicate to another project**.

.. figure:: /_static/task-duplication-another-project.png
   :alt: Task Duplication Another Project

Only projects where you are members will be shown in the drop-down.

Before to copy the tasks, Kanboard will ask you the destination
properties that are not common between the source and destination
project.

Basically, you need to define:

-  The destination swim lane
-  The column
-  The category
-  The assignee

Move a task to another project
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Go to the task view and choose **Move to another project**.

Moving a task to another project work in the same way as the
duplication, you have to choose the new properties of the task.

List of duplicated properties
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  title
-  description
-  date_due
-  color_id
-  project_id
-  column_id
-  owner_id
-  score
-  category_id
-  time_estimated
-  swimlane_id
-  recurrence_status
-  recurrence_trigger
-  recurrence_factor
-  recurrence_timeframe
-  recurrence_basedate

Closing Tasks
-------------

When a task is closed, it is hidden from the board.

However, you can always access to the list of closed tasks by using the
query **status:closed** in any search form or simply choose **Closed
tasks** from the filter drop-down.

There are two different ways to close a task, from the task drop-down
menu on the board:

.. figure:: /_static/menu-close-task.png
   :alt: Close a task from drop-down menu

Or from the task sidebar menu in the task detail view:

.. figure:: /_static/closing-tasks.png
   :alt: Close task

Note: When you close a task, all sub-tasks not completed will be changed
to the status "Done".

Internal Task Links
-------------------

Tasks can be linked together with pre-defined relationships:

.. figure:: /_static/internal-task-links.png
   :alt: Task Links

This is also possible to link tasks across projects.

The default relationships are:

-  **relates to**
-  **blocks** \| is blocked by
-  **is blocked by** \| blocks
-  **duplicates** \| is duplicated by
-  **is duplicated by** \| duplicates
-  **is a child of** \| is a parent of
-  **is a parent of** \| is a child of
-  **targets milestone** \| is a milestone of
-  **is a milestone of** \| targets milestone
-  **fixes** \| is fixed by
-  **is fixed by** \| fixes

Those labels can be changed in the application settings.

Task Transitions
----------------

Each movement of a task between columns is recorded in the database.

.. figure:: /_static/task-transitions.png
   :alt: Task Transitions

Available from the task view, you can see that information:

-  Date of the action
-  Source column
-  Destination column
-  Executor (users that moves the task)
-  Time spent in the origin column

Recurring Tasks
---------------

To fit with the Kanban methodology, the recurring tasks are not based on
a date but on board events.

-  Recurring tasks are duplicated to the first column of the board when
   the selected events occur
-  The due date can be recalculated automatically
-  Each task records the task id of the parent task that created it and
   the child task created

Configuration
~~~~~~~~~~~~~

Go to the task view page or use the drop-down menu on the board, then
select **Edit recurrence**.

.. figure:: /_static/recurring-tasks.png
   :alt: Recurring task

There are 3 triggers that currently create a new recurring task:

-  Moving a task from the first column
-  Moving a task to the last column
-  Closing the task

Due dates, if set on the current task, can be recalculated by a given
factor of days, months or years. The base date for the calculation of
the new due date can be either the existing due date, or the action
date.

Adding Screenshots
------------------

You can copy and paste images directly in Kanboard to save time. These
images are uploaded as attachments to the task.

This is especially useful for taking screenshots to describe an issue
for example.

You can add screenshots directly from the board by clicking on the
dropdown menu or in the task view page.

.. figure:: /_static/dropdown-screenshot.png
   :alt: Drop-down screenshot menu

To add a new image, take your screenshot and paste with CTRL+V or
Command+V:

.. figure:: /_static/task-screenshot.png
   :alt: Screenshot page

On Mac OS X, you can use those shortcuts to take screenshots:

-  Command-Control-Shift-3: Take a screenshot of the screen, and save it
   to the clipboard
-  Command-Control-Shift-4, then select an area: Take a screenshot of
   the area and save it to the clipboard
-  Command-Control-Shift-4, then space, then click a window: Take a
   screenshot of a window and save it to the clipboard

There are also several third-party applications that can be used to take
screenshots with annotations and shapes.

.. warning::  **This feature doesn’t work with all browsers.**
              It does not work with Safari due to this bug: `<https://bugs.webkit.org/show_bug.cgi?id=49141>`_


Tags
----

With Kanboard, you can associate one or many tags to a task. You can
define tags globally for all projects or only for a specific project.

.. figure:: /_static/tags-board.png
   :alt: Tags on the board

From the task form, you can enter the desired tags:

.. figure:: /_static/tags-task.png
   :alt: Tags form

The auto-completion form will show up to suggest available tags.

You can also create tags directly from the task form. By default, when
you create tags from a task form they are associated to the current
project:

.. figure:: /_static/tags-projects.png
   :alt: Project Tags

All tags can be managed in the project settings.

To define tags globally for all projects, go to the application
settings:

.. figure:: /_static/tags-global.png
   :alt: Global Tags

To search tasks based on tags, just use the attribute “tag”:

.. figure:: /_static/tags-search.png
   :alt: Search Tags

Analytics
---------

Each task has an analytics section available from the left menu in the
task view.

Lead and Cycle Time
~~~~~~~~~~~~~~~~~~~

.. figure:: /_static/task-lead-cycle-time.png
   :alt: Lead and cycle time

-  The lead time is the time between the task creation and the date of
   completion (task closed).
-  The cycle time is the time between the start date and the date of
   completion.
-  If the task is not closed the current time is used instead of the
   date of completion.
-  If the start date is not specified, the cycle time is not calculated.

Note: You can configure an automatic action to define the start date
automatically when you move a task to the column of your choice.

Time Spent Into Each Column
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: /_static/time-into-each-column.png
   :alt: Time spent into each column

-  This chart shows the total time spent into each column for the task.
-  The time spent is calculated until the task is closed.
