---
title: Notifications
toc: true
---

Kanboard is able to send notifications through several channels:

- Email
- Web (List of unread messages)

External plugins allow you to send notifications to Slack, Hipchat,
Jabber or any chat system.

Configuration
-------------

Each user must enable the notifications in their profile: **User Profile > Notifications**. It's disabled by default.

To receive email notifications you need a valid email address in your profile and the application must be configured to send emails.

![Notifications](/images/v1/notifications.png)

You can choose your favorite notification method:

- Emails
- Web (see below)

For each project you are a member, you can choose to receive notifications for:

- All tasks
- Only for tasks assigned to you
- Only for tasks created by you
- Only for tasks created by you and assigned to you

You can also select only some projects, by default it's all projects where you are a member.

Web notifications
-----------------

Web notifications are available from the dashboard or from the icon at the top:

![Web Notification Icon](/images/v1/web-notifications-icon.png)

Notifications are shown in a list, so you can mark individual notification as read or everything.

![Web Notification](/images/v1/web-notifications.png)

In this way you can still get notified without having to receive emails.

User Mentions
-------------

Kanboard offers the possibility to send notifications when someone is
mentioned.

If you need to get the attention of someone in a comment or in a task,
use the @ symbol followed by their username. Kanboard will automatically
suggest a list of users:

![User Mentions](/images/v1/user-mentions.png)

- At the moment, only the task description and the comment text area have this feature enabled.
- The user mentions works only during tasks and comments creation.
- To be notified, mentioned users need to be a member of the project.
- When someone is mentioned, this user will receive a notification.
- The `@username` mention is linked to the public user profile.

The notification is sent according to the user settings, it can be an email, a web notification or even a message on Slack/Hipchat/Jabber if you have installed these plugins.
