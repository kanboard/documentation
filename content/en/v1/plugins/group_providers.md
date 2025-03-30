---
title: Custom Group Providers
toc: true
menu:
    main:
        parent: Developing Plugins
---

Kanboard can load groups from an external system. This feature is primarily used for project permissions.

Project managers can grant access to a project for a group. The end-user uses an auto-complete box to search for a group.

Each time a group query is executed, all registered group providers are queried.

Group Provider Workflow
-----------------------

1. The end-user starts typing the group name in the auto-complete field.
2. The `GroupManager` class executes the query across all registered group providers.
3. Results are merged and returned to the user interface.
4. After selecting a group, the group's information is synced to the local database if necessary.

Group Provider Interface
------------------------

Interface to implement: `Kanboard\Core\Group\GroupProviderInterface`.

Classes that implement this interface abstract the group information. There are only three methods:

- `getInternalId()`: Gets the internal database ID; returns 0 otherwise.
- `getExternalId()`: Gets the external unique ID.
- `getName()`: Gets the group name.

Kanboard uses the external ID to sync with the local database.

Group Backend Provider Interface
--------------------------------

Interface to implement: `Kanboard\Core\Group\GroupBackendProviderInterface`.

This interface requires only one method: `find($input)`. The argument `$input` is the text entered by the user in the interface.

This method must return a list of `GroupProviderInterface` instances, which represent the search results.

Backend Registration from Plugins
---------------------------------

In the `initialize()` method of your plugin, register your custom backend like this:

```php
$groupManager->register(new MyCustomLdapBackendGroupProvider($this->container));
```

Examples
--------

- [Group providers included in Kanboard (LDAP and Database)](https://github.com/kanboard/kanboard/tree/main/app/Group)
