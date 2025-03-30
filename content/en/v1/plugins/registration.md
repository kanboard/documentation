---
title: Plugin Registration
toc: true
menu:
    main:
        parent: Developing Plugins
---

Project Skeleton Generator
--------------------------

You can use `cookiecutter` to automatically create the project structure for your plugin.

### Install Cookiecutter

```bash
pip install -U cookiecutter
```

### Run Kanboard Cookiecutter

```bash
cookiecutter gh:kanboard/cookiecutter-plugin
plugin_name [My Plugin]: Some Plugin
plugin_namespace [MyPlugin]: SomePlugin
plugin_author [Plugin Author]: Me
plugin_description [My plugin is awesome]:
plugin_homepage [https://github.com/kanboard/plugin-myplugin]:
```

Directory Structure
-------------------

Plugins are stored in the `plugins` subdirectory. Below is an example of a plugin directory structure:

```
plugins
└── Budget            <= Plugin name
    ├── Asset         <= JavaScript/CSS files
    ├── Controller
    ├── LICENSE       <= Plugin license
    ├── Locale
    │   ├── fr_FR
    │   ├── it_IT
    │   ├── ja_JP
    │   └── zh_CN
    ├── Model
    ├── Plugin.php    <= Plugin registration file
    ├── README.md
    ├── Schema        <= Database migrations
    ├── Template
    └── Test          <= Unit tests
```

Only the registration file `Plugin.php` is required. Other folders are optional.

The first letter of the plugin name must be capitalized.

Plugin Registration File
------------------------

Kanboard scans the `plugins` directory and automatically loads everything under it. The file `Plugin.php` is used to load and register the plugin.

Example of a `Plugin.php` file (`plugins/Foobar/Plugin.php`):

```php
<?php

namespace Kanboard\Plugin\Foobar;

use Kanboard\Core\Plugin\Base;

class Plugin extends Base
{
    public function initialize()
    {
        $this->template->hook->attach('template:layout:head', 'theme:layout/head');
    }

    public function getCompatibleVersion()
    {
        // Examples:
        // >=1.0.37
        // <1.0.37
        // <=1.0.37
        return '1.0.37';
    }
}
```

This file must contain a `Plugin` class defined under the namespace `Kanboard\Plugin\Yourplugin` and extend `Kanboard\Core\Plugin\Base`.

The only required method is `initialize()`. This method is called for each request when the plugin is loaded.

Plugin Methods
--------------

Available methods from `Kanboard\Core\Plugin\Base`:

- `initialize()`: Executed when the plugin is loaded.
- `getClasses()`: Returns all classes that should be stored in the dependency injection container.
- `on($event, $callback)`: Listens to internal events.
- `getPluginName()`: Returns the plugin name (must match the `plugins.json` `"title":` entry for "Plugin Directory" version update notifications to work).
- `getPluginAuthor()`: Returns the plugin author.
- `getPluginVersion()`: Returns the plugin version.
- `getPluginDescription()`: Returns the plugin description.
- `getPluginHomepage()`: Returns the plugin homepage (link).
- `setContentSecurityPolicy(array $rules)`: Overrides default HTTP CSP rules.
- `onStartup()`: If present, this method is executed automatically when the event `app.bootstrap` is triggered.
- `getCompatibleVersion()`: Specifies the Kanboard version compatible with the plugin.

Your plugin registration class can also inherit from `Kanboard\Core\Base`, allowing you to access all classes and methods of Kanboard easily.

For example, to fetch user #123:

```php
$this->user->getById(123);
```

Plugin Translations
-------------------

Plugins can be translated in the same way as the rest of the application. You must load the translations yourself when the session is created:

```php
public function onStartup()
{
    Translator::load($this->languageModel->getCurrentLanguage(), __DIR__.'/Locale');
}
```

Translations must be stored in the file `plugins/Myplugin/Locale/xx_XX/translations.php` (replace `xx_XX` with the language code, e.g., `fr_FR`, `en_US`).

Translations are stored in a dictionary. To override an existing string, use the same key in your translation file.

Dependency Injection Container
------------------------------

Kanboard uses Pimple, a simple PHP Dependency Injection Container. However, Kanboard can easily register any class in the container.

These classes are available throughout the application, and only one instance is created.

Here is an example of registering your own models in the container:

```php
public function getClasses()
{
    return array(
        'Plugin\Budget\Model' => array(
            'HourlyRateModel',
            'BudgetModel',
        )
    );
}
```

Now, if you use a class that extends `Core\Base`, you can directly access those class instances:

```php
$this->hourlyRateModel->remove(123);
$this->budgetModel->getDailyBudgetBreakdown(456);

// This is equivalent to using the container:
$this->container['hourlyRateModel']->getAll();
```

Keys in the container are unique across the application. If you override an existing class, you will change its default behavior.
