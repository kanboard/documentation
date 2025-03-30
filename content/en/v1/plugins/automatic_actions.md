---
title: Adding Automatic Actions
toc: true
menu:
    main:
        parent: Developing Plugins
---

Adding a new automatic action is straightforward.

Creating a new action
---------------------

Your automatic action must inherit from the class `Kanboard\Action\Base`.
Several abstract methods must be implemented by you:

Method                               | Description
-------------------------------------| -------------------------------------
`getDescription()`                   | Description visible in the user interface
`getCompatibleEvents()`              | List of compatible events
`getActionRequiredParameters()`      | Required parameters for the action (defined by the user)
`getEventRequiredParameters()`       | Required parameters for the event
`doAction(array $data)`              | Executes the action; must return `true` on success
`hasRequiredCondition(array $data)`  | Checks if the event data meets the action condition

Your automatic action is identified in Kanboard by using the fully qualified class name, including the namespace.

Adding new events
-----------------

The list of application events is available in the class `Kanboard\Core\Event\EventManager::getAll()`. However, if your plugin fires new events, you can register these events like this:

```php
$this->actionManager->getAction('\Kanboard\Plugin\MyPlugin\MyActionName')->addEvent('my.event', 'My event description');
```

You can extend the list of compatible events for existing actions using the same method.

Registering the action
----------------------

You must call the `register()` method from the class `Kanboard\Core\Action\ActionManager`:

```php
<?php

namespace Kanboard\Plugin\AutomaticAction;

use Kanboard\Core\Plugin\Base;
use Kanboard\Plugin\AutomaticAction\Action\TaskRename;

class Plugin extends Base
{
    public function initialize()
    {
        $this->actionManager->register(new TaskRename($this->container));
    }
}
```

Example
-------

- [Automatic Action example](https://github.com/kanboard/plugin-example-automatic-action)
