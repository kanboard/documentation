---
title: Authorization Architecture
toc: true
menu:
    main:
        parent: Developing Plugins
---

Kanboard supports multiple roles at both the application level and the project level.

Authorization Workflow
----------------------

For each HTTP request:

1. Authorize or deny access to the resource based on the application access list.
2. If the resource belongs to a project (e.g., board, task):
    1. Fetch the user's role for this project.
    2. Grant or deny access based on the project access map.

Extending the Access Map
------------------------

The Access List (ACL) is based on the controller class name and the method name. The list of accesses is managed by the class `Kanboard\Core\Security\AccessMap`.

There are two access maps: one for the application and another for projects.

- Application access map: `$this->applicationAccessMap`
- Project access map: `$this->projectAccessMap`

Examples of defining a new policy in your plugin:

```php
// Grant access to all methods of the class MyController:
$this->projectAccessMap->add('MyController', '*', Role::PROJECT_MANAGER);

// Grant access to specific methods:
$this->projectAccessMap->add('MyOtherController', array('create', 'save'), Role::PROJECT_MEMBER);
```

Roles are defined in the class `Kanboard\Core\Security\Role`.

The `Authorization` class (`Kanboard\Core\Security\Authorization`) checks access for each page.
