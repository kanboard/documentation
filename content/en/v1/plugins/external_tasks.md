---
title: External Task Providers
toc: true
menu:
    main:
        parent: Developing Plugins
---

Kanboard can be used to manage tasks stored in another system. For example, an external system can be a bug tracker or any kind of ticketing software. This allows you to use Kanboard to manage external tasks in the same way as native tasks.

Workflow
--------

Creation:

1. The end-user selects an alternative task provider during task creation.
2. The external task provider exposes a form to the user to fetch the external task.
3. The external task is retrieved from the other system.
4. A customized form is displayed to the user.

Visualization:

When the task detail page is opened, Kanboard will asynchronously load the remote task. This information may be cached by the plugin to improve loading time.

Modification:

Optionally, the plugin can provide a custom form to save additional information to the external system.

Interfaces
----------

External task providers must implement at least two interfaces:

- `Kanboard\Core\ExternalTask\ExternalTaskProviderInterface`
- `Kanboard\Core\ExternalTask\ExternalTaskInterface`

### ExternalTaskProviderInterface

Method                                               | Usage
-----------------------------------------------------| -----------------------------
`getName()`                                          | Get the provider name (label).
`fetch()`                                            | Retrieve a task from the external system or cache.
`save($uri, array $formValues, array &$formErrors)`  | Save the external task to another system.
`getImportFormTemplate()`                            | Get the task import template name.
`getCreationFormTemplate()`                          | Get the creation form template.
`getModificationFormTemplate()`                      | Get the modification form template.
`getViewTemplate()`                                  | Get the task view template name.
`buildTaskUri(array $formValues)`                    | Build the external task URI based on import form values.

### ExternalTaskInterface

Method               | Usage
---------------------| -------------------------------------------------
`getUri()`           | Return the Uniform Resource Identifier for the task.
`getFormValues()`    | Return a dictionary to populate the task form.

Exceptions
----------

The plugin may raise an exception if something goes wrong:

- `Kanboard\Core\ExternalTask\ExternalTaskException`: Generic error related to the external system.
- `Kanboard\Core\ExternalTask\AccessForbiddenException`: Access is not allowed by the external system.
- `Kanboard\Core\ExternalTask\NotFoundException`: External task not found.

Provider Registration
---------------------

```php
class Plugin extends Base
{
    public function initialize()
    {
        $this->externalTaskManager->register(new MyExternalTaskProvider());
    }
}
```
