Settings
========

Some parameters for the application can be changed on the settings page.
Only administrators can change those settings.

Application Settings
--------------------

Go to the menu **Settings**, then choose **Application settings** on the
left.

.. figure:: /_static/application-settings.png
   :alt: Application settings

Application URL
~~~~~~~~~~~~~~~

This parameter is used for email notifications. The email footer will
contain a link to the Kanboard task.

Language
~~~~~~~~

The application language can be changed at anytime. The language will be
set for all users.

Time zone
~~~~~~~~~

By default, Kanboard use UTC as time zone, but you can define your own
time zone. The list contains all supported time zones by your web
server.

Date format
~~~~~~~~~~~

Input format used for date fields, for examples the due date for tasks.

Kanboard offers 4 different formats:

-  DD/MM/YYYY
-  MM/DD/YYYY (default)
-  YYYY/MM/DD
-  MM.DD.YYYY

The `ISO 8601 <http://en.wikipedia.org/wiki/ISO_8601>`__ format is
always accepted (YYYY-MM-DD or YYYY_MM_DD).

Custom Stylesheet
~~~~~~~~~~~~~~~~~

Write your own CSS to override or improve Kanboard default style.

Here an example to change color of category labels:

For the category container:

.. code:: css

    .task-board-category-container-color span {
      border: solid 0.5px grey;
      color: black;
    }

Custom css values for one category - this is an example for displaying
the text:

.. code:: css

    [class*="category-MyLabel"] {
      background-color: rgba(255, 0, 0, 0.50);
      border: none!important;
      font-weight: bold;
      font-style: italic;
      box-shadow: 0 1px 1px rgba(186, 186, 186, 0.55);
      color: white!important;
      font-size:11px;
    }

Project Settings
----------------

Go to the menu **Settings**, then choose **Project settings** on the
left.

.. figure:: /_static/project-settings.png
   :alt: Project settings

Default columns for new projects
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can change the default column names here. It’s useful if you always
create projects with the same columns.

Each column name must be separated by a comma.

By default, Kanboard use those column names: Backlog, Ready, Work in
progress and Done.

Default categories for new projects
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Categories are not global to the application but attached to a project.
Each project can have different categories.

However, if you always create the same categories for all your projects,
you can define here the list of categories to create automatically.

Allow only one subtask in progress at the same time for a user
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When this option is enabled, a user can work with only one subtask at
the time.

If another subtask have the status “in progress”, the user will see this
dialog box:

.. figure:: /_static/subtask-user-restriction.png
   :alt: Subtask user restriction

Trigger automatically subtask time tracking
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  If enabled, when a subtask status is changed to “in progress”, the
   timer will start automatically.
-  Disable this option if you don’t use time tracking.

Include closed tasks in the cumulative flow diagram
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  If enabled, closed tasks will be included in the cumulative flow
   diagram.
-  If disabled, only open tasks will be included.
-  This option affects the column “total” of the table
   “project_daily_column_stats”

Board Settings
--------------

Go to the menu **Settings**, then choose **Board settings** on the left.

.. figure:: /_static/board-settings.png
   :alt: Board settings

Task highlighting
~~~~~~~~~~~~~~~~~

This feature displays a shadow around the task when a task is moved
recently.

Set the value 0 to disable this feature, 2 days by default (172800
seconds).

Everything moved since 2 days will have shadow around the task.

Refresh interval for public board
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When you share a board, the page will refresh every 60 seconds
automatically by default.

Refresh interval for private board
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When your web browser is open on a board, Kanboard checks every 10
seconds if something has been changed by someone else.

Technically this process is done by Ajax polling.

Calendar Settings
-----------------

Go to the menu **Settings**, then choose **Calendar settings** on the
left.

.. figure:: /_static/calendar-settings.png
   :alt: Calendar settings

There are two different calendars in Kanboard:

-  Project calendar
-  User calendar (available from the dashboard)

Project Calendar
~~~~~~~~~~~~~~~~

This calendar shows tasks with defined due date and tasks based on the
creation date or the start date.

Show tasks based on the creation date:

-  The start date of the calendar event is the creation date of the
   task.
-  The end date of the event is the date of completion.

Show tasks based on the start date:

-  The start date of the calendar event is the start date of the task.
-  This date can be defined manually.
-  The end date of the event is the date of completion.
-  If there is no start date the task will not appear on the calendar.

User Calendar
~~~~~~~~~~~~~

This calendar shows only tasks assigned to the user and optionally
sub-tasks information.

Show sub-tasks based on the time tracking:

-  Display sub-tasks in the calendar from the information recorded in
   the time tracking table.
-  The intersection with the user timetable is also calculated.

Show sub-task estimates (forecast of future work):

-  Display the estimate of future work for sub-tasks in status “todo”
   and with a defined “estimate” value.

Link Settings
-------------

Task relations can be changed from the application settings (**Settings
> Link settings**)

.. figure:: /_static/link-labels.png
   :alt: Link Labels

Each label may have an opposite label defined. If there is no opposite,
the label is considered bidirectionnal.

.. figure:: /_static/link-label-creation.png
   :alt: Link Label Creation
