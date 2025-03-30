---
title: Avatar Providers
toc: true
menu:
    main:
        parent: Developing Plugins
---

Registration
------------

```php
$this->avatarManager->register(new CustomAvatarProvider());
```

Interface
---------

The provider must implement the interface `Kanboard\Core\User\Avatar\AvatarProviderInterface`:

Method                        | Description
------------------------------| ------------------------------------------
`render(array $user, $size)`  | Renders HTML
`isActive(array $user)`       | Returns a boolean indicating if the provider can render something

The `$user` argument is an array that contains the following keys:

```php
[
    'id' => 123,
    'username' => 'admin',
    'name' => 'Administrator',
    'email' => 'me@localhost',
]
```
