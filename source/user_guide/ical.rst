iCalendar Subscriptions
=======================

Kanboard supports iCal feeds for projects and users. This feature allows
you to import Kanboard tasks in almost any calendar program (Microsoft 
Outlook, Apple Calendar, Mozilla Thunderbird and Google
Calendar).

Calendar subscriptions are **read-only** access, you cannot create tasks
from external calendar software. The Calendar feed export follows the
iCal standard.

Note: Only tasks within the date range of -2 months to +6 months are
exported to the iCalendar feed.

Project Calendars
-----------------

-  Each project has its own calendar.
-  The subscription link is unique per project, the link is activated
   when you enable the public access of your project: **Project settings
   > Public access**.
-  This calendar shows only tasks for the selected project.

User Calendars
--------------

-  Each user has its own calendar.
-  The subscription link is unique per user, the link is activated when
   you enable the public access of your user: **User profile > Public
   access**.
-  This calendar show tasks assigned to the user for all projects.

Adding your Kanboard Calendar to Apple Calendar
-----------------------------------------------

-  Open Calendar
-  Select **File > New Calendar Subscription**
-  Copy and paste the iCal feed URL from Kanboard

.. figure:: /_static/apple-calendar-add-subscription.png
   :alt: Add iCal subscription

-  You can choose to synchronize the calendar with iCloud to be
   available across all your devices
-  Don’t forget to select the refresh frequency

.. figure:: /_static/apple-calendar-edit-subscription.png
   :alt: Edit iCal subscription

Adding your Kanboard Calendar to Mozilla Thunderbird
----------------------------------------------------

-  Click on **File > New > Calendar**
-  In the dialog box, choose **On the Network**

.. figure:: /_static/thunderbird-new-calendar-step1.png
   :alt: Thunderbird Step 1

-  Copy and paste the iCal feed URL from Kanboard

.. figure:: /_static/thunderbird-new-calendar-step2.png
   :alt: Thunderbird Step 2

Adding your Kanboard calendar to Google Calendar
------------------------------------------------

-  Click the down-arrow next to **Other calendars**.
-  Select **Add by URL** from the menu.
-  Copy and paste the iCal feed URL from Kanboard

.. figure:: /_static/google-calendar-add-subscription.png
   :alt: Google Calendar

Your Kanboard calendar can also be available from your Android device if
you enable the synchronization.

Note: According to the Google Support, external calendars are not
refreshed very often, `read the
documentation <https://support.google.com/calendar/answer/37100?hl=en&ref_topic=1672445>`__.
