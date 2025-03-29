---
title: iCalendar Subscriptions
toc: true
menu:
    main:
        parent: Using Kanboard
---

Kanboard supports iCal feeds for projects and users.
This feature allows you to import Kanboard tasks into almost any calendar program (Microsoft Outlook, Apple Calendar, Mozilla Thunderbird, and Google Calendar).

Calendar subscriptions provide **read-only** access; you cannot create tasks from external calendar software. The calendar feed export follows the iCal standard.

Note: Only tasks within the date range of -2 months to +6 months are exported to the iCalendar feed.

Project Calendars
-----------------

- Each project has its own calendar.
- The subscription link is unique per project and is activated when you enable public access for your project: **Project settings > Public access**.
- This calendar shows only tasks for the selected project.

User Calendars
--------------

- Each user has their own calendar.
- The subscription link is unique per user and is activated when you enable public access for your user: **User profile > Public access**.
- This calendar shows tasks assigned to the user across all projects.

Adding Your Kanboard Calendar to Apple Calendar
-----------------------------------------------

- Open Calendar.
- Select **File > New Calendar Subscription**.
- Copy and paste the iCal feed URL from Kanboard.

![Add Kanboard iCal feed to Apple Calendar](/images/v1/apple-calendar-add-subscription.png)

- You can choose to synchronize the calendar with iCloud to make it available across all your devices.
- Don't forget to select the refresh frequency.

![Edit Apple Calendar Subscription](/images/v1/apple-calendar-edit-subscription.png)

Adding Your Kanboard Calendar to Mozilla Thunderbird
----------------------------------------------------

- Click on **File > New > Calendar**.
- In the dialog box, choose **On the Network**.

![First Step to Add Calendar on Thunderbird](/images/v1/thunderbird-new-calendar-step1.png)

- Copy and paste the iCal feed URL from Kanboard.

![Second Step to Add Calendar to Thunderbird](/images/v1/thunderbird-new-calendar-step2.png)

Adding Your Kanboard Calendar to Google Calendar
------------------------------------------------

- Click the down-arrow next to **Other calendars**.
- Select **Add by URL** from the menu.
- Copy and paste the iCal feed URL from Kanboard.

![Add iCal feed to Google Calendar](/images/v1/google-calendar-add-subscription.png)

Your Kanboard calendar can also be available on your Android device if you enable synchronization.

Note: According to Google Support, external calendars are not refreshed very often. [Read the documentation](https://support.google.com/calendar/answer/37100?hl=en&ref_topic=1672445).
