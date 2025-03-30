---
title: Custom Routes
toc: true
menu:
    main:
        parent: Developing Plugins
---

When URL rewriting is enabled, you can define custom routes in your plugins.

Define new routes
-----------------

Routes are handled by the class `Kanboard\Core\Http\Route`.

New routes can be added using the method `addRoute($path, $controller, $action, $plugin)`. Here is an example:

```php
$this->route->addRoute('/my/custom/route', 'myController', 'myAction', 'myplugin');
```

When the end-user navigates to the URL `/my/custom/route`, the method `Kanboard\Plugin\Myplugin\Controller\MyController::myAction()` will be executed.

The first character of the controller and the plugin name will be converted to uppercase with the function `ucfirst()`.

You can also define routes with variables:

```php
$this->route->addRoute('/my/route/:my_variable', 'myController', 'myAction', 'myplugin');
```

The colon prefix `:`, defines a variable. For example, `:my_variable` declares a new variable named `my_variable`.

To fetch the value of the variable, you can use the method `getStringParam()` or `getIntegerParam()` from the class `Kanboard\Core\Http\Request`:

If we have the URL `/my/route/foobar`, the value of `my_variable` is `foobar`:

```php
$this->request->getStringParam('my_variable'); // Returns foobar
```

Generate links based on the routing table
-----------------------------------------

From templates, you have to use the helper `Kanboard\Helper\Url`.

### Generate an HTML link

```php
<?= $this->url->link('My link', 'mycontroller', 'myaction', array('plugin' => 'myplugin')) ?>
```

This will generate the following HTML:

```
<a href="/my/custom/route">My link</a>
```

### Generate only the `href` attribute:

```php
<?= $this->url->href('My link', 'mycontroller', 'myaction', array('plugin' => 'myplugin')) ?>
```

HTML output:

```
/my/custom/route
```

HTML output when URL rewriting is not enabled:

```
?controller=mycontroller&amp;action=myaction&amp;plugin=myplugin
```

### Generate a redirect link:

From a controller, if you need to perform a redirection:

```php
$this->url->to('mycontroller', 'myaction', array('plugin' => 'myplugin'));
```

This generates:

```
?controller=mycontroller&action=myaction&plugin=myplugin
```
