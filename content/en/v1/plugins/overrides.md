---
title: Plugin Overrides
toc: true
menu:
    main:
        parent: Developing Plugins
---

Override HTTP Content Security Policy
-------------------------------------

To replace the default HTTP Content Security Policy header, use the `setContentSecurityPolicy()` method:

```php
<?php

namespace Kanboard\Plugin\Csp;

use Kanboard\Core\Plugin\Base;

class Plugin extends Base
{
    public function initialize()
    {
        $this->setContentSecurityPolicy(array('script-src' => 'something'));
    }
}
```

Template Overrides
------------------

Core templates can be overridden. For example, you can redefine the default layout or modify email notifications.

Example of a template override:

```php
$this->template->setTemplateOverride('header', 'theme:layout/header');
```

The first argument is the original template name, and the second argument is the replacement template.

To use the original template, prefix it with "kanboard:":

```php
<?= $this->render('kanboard:header') ?>
```

Formatter Overrides
-------------------

Here is an example of overriding formatter objects in Kanboard:

```php
class MyFormatter extends UserAutoCompleteFormatter
{
    public function format()
    {
        $users = parent::format();

        foreach ($users as &$user) {
            $user['label'] = 'something'; // Modify the user label as needed
        }

        return $users;
    }
}

class Plugin extends Base
{
    public function initialize()
    {
        $this->container['userAutoCompleteFormatter'] = $this->container->factory(function ($c) {
            return new MyFormatter($c);
        });
    }
}
```
