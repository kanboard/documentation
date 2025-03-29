---
title: Notifications
toc: true
menu:
    main:
        parent: Using Kanboard
---

Kanboard can send notifications through several channels:

- Email
- Web (List of unread messages)

External plugins allow you to send notifications to Slack, Hipchat, Jabber, or any chat system.

Configuration
-------------

Each user must enable notifications in their profile: **User Profile > Notifications**. Notifications are disabled by default.

To receive email notifications, you need a valid email address in your profile, and the application must be configured to send emails.

![Notifications](/images/v1/notifications.png)

You can choose your preferred notification method:

- Emails
- Web (see below)

For each project you are a member of, you can choose to receive notifications for:

- All tasks
- Only tasks assigned to you
- Only tasks created by you
- Only tasks created by you and assigned to you

You can also select specific projects. By default, notifications are enabled for all projects where you are a member.

Web Notifications
-----------------

Web notifications are available from the dashboard or the icon at the top:

![Web Notification Icon](/images/v1/web-notifications-icon.png)

Notifications are shown in a list, allowing you to mark individual notifications as read or mark all as read.

![Web Notification](/images/v1/web-notifications.png)

This way, you can stay notified without receiving emails.

User Mentions
-------------

Kanboard offers the ability to send notifications when someone is mentioned.

If you need to get someone's attention in a comment or task, use the `@` symbol followed by their username. Kanboard will automatically suggest a list of users:

![User Mentions](/images/v1/user-mentions.png)

- Currently, only the task description and the comment text area have this feature enabled.
- User mentions work only during task and comment creation.
- To be notified, mentioned users must be members of the project.
- When someone is mentioned, they will receive a notification.
- The `@username` mention links to the public user profile.

Notifications are sent according to the user's settings. They can be emails, web notifications, or messages on Slack/Hipchat/Jabber if these plugins are installed.
