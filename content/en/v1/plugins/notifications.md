---
title: Add Notification Types with Plugins
toc: true
menu:
    main:
        parent: Developing Plugins
---

You can send notifications to almost any system by adding a new type.
There are two kinds of notifications: `project` and `user`.

- **Project**: Notifications configured at the project level.
- **User**: Notifications sent individually and configured in the user profile.

Register a New Notification Type
--------------------------------

In your plugin registration file, call the method `setType()`:

```php
$this->userNotificationTypeModel->setType('irc', t('IRC'), '\Kanboard\Plugin\IRC\Notification\IrcHandler');
$this->projectNotificationTypeModel->setType('irc', t('IRC'), '\Kanboard\Plugin\IRC\Notification\IrcHandler');
```

Your handler can be registered for user or project notifications. You don't necessarily need to support both.

Once your handler is registered, the end-user can choose whether to receive the new notification type.

Notification Handler
--------------------

Your notification handler must implement the interface `Kanboard\Core\Notification\NotificationInterface`:

```php
interface NotificationInterface
{
    /**
     * Send a notification to a user.
     *
     * @access public
     * @param  array     $user
     * @param  string    $event_name
     * @param  array     $event_data
     */
    public function notifyUser(array $user, $event_name, array $event_data);

    /**
     * Send a notification to a project.
     *
     * @access public
     * @param  array     $project
     * @param  string    $event_name
     * @param  array     $event_data
     */
    public function notifyProject(array $project, $event_name, array $event_data);
}
```

Examples of Notification Plugins
--------------------------------

- [Slack](https://github.com/kanboard/plugin-slack)
- [Hipchat](https://github.com/kanboard/plugin-hipchat)
- [Jabber](https://github.com/kanboard/plugin-jabber)
