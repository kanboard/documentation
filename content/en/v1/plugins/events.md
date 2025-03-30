---
title: Using Events
toc: true
menu:
    main:
        parent: Developing Plugins
---

Kanboard uses the [Symfony EventDispatcher component](https://symfony.com/doc/2.3/components/event_dispatcher/index.html) internally to manage events.

Event Listening
---------------

```php
$this->on('app.bootstrap', function($container) {
    // Do something
});
```

- The first argument is the event name (a string).
- The second argument is a PHP callable function (a closure or class method).

Adding a New Event
------------------

To add a new event, call the `register()` method of the `Kanboard\Core\Event\EventManager` class:

```php
$this->eventManager->register('my.event.name', 'My new event description');
```

These events can be used by other components of Kanboard, such as automatic actions.
