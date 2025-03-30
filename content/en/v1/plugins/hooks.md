---
title: Plugin Hooks
toc: true
menu:
    main:
        parent: Developing Plugins
---

Add New API Methods
-------------------

Kanboard uses the library [JSON-RPC](https://github.com/kanboard/kanboard/tree/main/libs/jsonrpc) to handle API calls.

To add a new method, you can do something like this in your plugin:

```php
$this->api->getProcedureHandler()->withCallback('my_method', function() {
    return 'foobar';
});
```

`$this->container['api']` or `$this->api` exposes an instance of the object `JsonRPC\Server`.

Refer to the library documentation for more information.

Add New Console Commands
------------------------

Kanboard uses the library [Symfony Console](http://symfony.com/doc/current/components/console/introduction.html) to handle local command-line operations.

Kanboard exposes an instance of the object `Symfony\Component\Console\Application` via `$this->cli`. You can add new commands in your plugin:

```php
$this->cli->add(new MyCommand());
```

Refer to the library documentation for more information.

Add New Task Filters
--------------------

Since the task lexer is a factory that returns a new instance each time, you must extend the `taskLexer` container using the `extend()` method of Pimple.

Here is an example:

```php
public function initialize()
{
    $this->container->extend('taskLexer', function($taskLexer, $c) {
        $taskLexer->withFilter(TaskBoardDateFilter::getInstance($c)->setDateParser($c['dateParser']));
        return $taskLexer;
    });
}
```

For the filter class implementation, there are several examples in the source code under the namespace `Kanboard\Filter`.

Application Hooks
-----------------

Hooks can extend, replace, filter data, or change the default behavior. Each hook is identified by a unique name, e.g., `controller:calendar:user:events`.

### Listen to Hook Events

In your `initialize()` method, call the `on()` method of the class `Kanboard\Core\Plugin\Hook`:

```php
$this->hook->on('hook_name', $callable);
```

The first argument is the name of the hook, and the second is a PHP callable.

### Hooks Executed Only Once

Some hooks can have only one listener, e.g., `model:subtask-time-tracking:calculate:time-spent`.

- Overrides time spent calculation when the sub-task timer is stopped.
- Arguments:
    - `$user_id` (integer)
    - `$start` (DateTime)
    - `$end` (DateTime)

Merge Hooks
-----------

"Merge hooks" act like the `array_merge` function. The hook callback must return an array, which will be merged with the default one.

Example to add events to the user calendar:

```php
class Plugin extends Base
{
    public function initialize()
    {
        $container = $this->container;

        $this->hook->on('controller:calendar:user:events', function($user_id, $start, $end) use ($container) {
            $model = new SubtaskForecast($container);
            return $model->getCalendarEvents($user_id, $end); // Return new events
        });
    }
}
```

Example to override default values for task forms:

```php
class Plugin extends Base
{
    public function initialize()
    {
        $this->hook->on('controller:task:form:default', function (array $default_values) {
            return empty($default_values['score']) ? array('score' => 4) : array();
        });
    }
}
```

List of merging hooks:

- `controller:task:form:default`
    - Overrides default values for task forms.
    - Arguments:
        - `$default_values`: current default values (array).

- `controller:calendar:project:events`
    - Adds more events to the project calendar.
    - Arguments:
        - `$project_id` (integer).
        - `$start` Calendar start date (string, ISO-8601 format).
        - `$end` Calendar end date (string, ISO-8601 format).

- `controller:calendar:user:events`
    - Adds more events to the user calendar.
    - Arguments:
        - `$user_id` (integer).
        - `$start` Calendar start date (string, ISO-8601 format).
        - `$end` Calendar end date (string, ISO-8601 format).

Asset Hooks
-----------

Asset hooks can be used to easily add a new stylesheet or JavaScript file to the layout. You can use this feature to create a theme and override all Kanboard default styles.

Example to add a new stylesheet:

```php
<?php

namespace Kanboard\Plugin\Css;

use Kanboard\Core\Plugin\Base;

class Plugin extends Base
{
    public function initialize()
    {
        $this->hook->on('template:layout:css', array('template' => 'plugins/Css/skin.css'));
    }
}
```

List of asset hooks:

- `template:layout:css`
- `template:layout:js`

Reference Hooks
---------------

Reference hooks pass a variable by reference.

Example:

```php
$this->hook->on('formatter:board:query', function (\PicoDb\Table &$query) {
    $query->eq(TaskModel::TABLE.'color_id', 'red');
});
```

The code above will show only tasks in red on the board.

List of reference hooks:

Hook                                  | Description
--------------------------------------| -------------------------------------------
`formatter:board:query`               | Alters database query before rendering the board.
`pagination:dashboard:project:query`  | Alters database query for project pagination on the dashboard.
`pagination:dashboard:task:query`     | Alters database query for task pagination on the dashboard.
`pagination:dashboard:subtask:query`  | Alters database query for subtask pagination on the dashboard.
`model:task:creation:prepare`         | Alters form values before saving a task.
`model:task:creation:aftersave`       | Retrieves Task ID after creating a task.
`model:task:modification:prepare`     | Alters form values before editing a task.
`model:task:duplication:aftersave`    | After task duplication.
`model:color:get-list`                | Alters default color values.
`model:subtask:modification:prepare`  | Alters form values before saving a subtask.
`model:subtask:creation:prepare`      | Alters form values before editing a subtask.
`model:subtask:count:query`           | Alters database query for subtask count.

Template Hooks
--------------

Template hooks allow additional content in existing templates.

Example to add new content in the dashboard sidebar:

```php
$this->template->hook->attach('template:dashboard:sidebar', 'myplugin:dashboard/sidebar');
```

Example to attach a template with local variables:

```php
$this->template->hook->attach('template:dashboard:sidebar', 'myplugin:dashboard/sidebar', [
    'variable' => 'foobar',
]);
```

Example to attach a template with a callable:

```php
$this->template->hook->attachCallable('template:dashboard:sidebar', 'myplugin:dashboard/sidebar', function($hook_param1, $hook_param2) {
    return ['new_template_variable' => 'foobar']; // Inject a new variable into the plugin template
});
```

This call is usually defined in the `initialize()` method. The first argument is the name of the hook, and the second argument is the template name.

Template names prefixed with the plugin name and colon indicate the location of the template.

Example with `myplugin:dashboard/sidebar`:

- `myplugin` is the name of your plugin (lowerCamelCase).
- `dashboard/sidebar` is the template name.
- On the filesystem, the plugin will be located here:
    `plugins\Myplugin\Template\dashboard\sidebar.php`.
- Templates are written in pure PHP (don't forget to escape data).

Template names without a prefix are core templates.

List of template hooks:

Hook                                                             | Description
-----------------------------------------------------------------| --------------------------
`template:analytic:sidebar`                                      | Sidebar on analytic pages.
`template:app:filters-helper:before`                             | Filter helper dropdown (top).
`template:app:filters-helper:after`                              | Filter helper dropdown (bottom).
`template:auth:login-form:before`                                | Login page (top).
`template:auth:login-form:after`                                 | Login page (bottom).
`template:board:private:task:before-title`                       | Task in private board before title.
`template:board:private:task:after-title`                        | Task in private board after title.
`template:board:public:task:before-title`                        | Task in public board before title.
`template:board:public:task:after-title`                         | Task in public board after title.
`template:board:task:footer`                                     | Task in board: footer.
`template:board:task:icons`                                      | Task in board: tooltip icon.
`template:board:table:column:before-header-row`                  | Row before board column header.
`template:board:table:column:after-header-row`                   | Row after board column header.
`template:board:column:dropdown`                                 | Dropdown menu in board columns.
`template:board:column:header`                                   | Board column header.
`template:board:tooltip:subtasks:header:before-assignee`         | Header of Subtask table on tooltip before Assignee.
`template:board:tooltip:subtasks:rows`                           | Column on row of Subtask table on tooltip.
`template:config:sidebar`                                        | Sidebar on settings page.
`template:config:application`                                    | Application settings form.
`template:config:board`                                          | Board settings form.
`template:config:email`                                          | Email settings page.
`template:config:integrations`                                   | Integration page in global settings.
`template:dashboard:show`                                        | Main page of the dashboard.
`template:dashboard:page-header:menu`                            | Dashboard submenu.
`template:dashboard:project:after-title`                         | Dashboard project after title.
`template:dashboard:project:before-title`                        | Dashboard project before title.
`template:dashboard:show:after-filter-box`                       | Dashboard after filter box.
`template:dashboard:show:before-filter-box`                      | Dashboard before filter box.
`template:dashboard:task:footer`                                 | Task in dashboard: footer.
`template:dashboard:sidebar`                                     | Dashboard sidebar.
`template:export:header`                                         | Export header.
`template:header:dropdown`                                       | Page header dropdown menu (user avatar icon).
`template:header:creation-dropdown`                              | Page header dropdown menu (plus icon).
`template:layout:head`                                           | Page layout `<head/>` tag.
`template:layout:top`                                            | Page layout top header.
`template:layout:bottom`                                         | Page layout footer.
`template:project:dropdown`                                      | "Actions" menu on the left in different project views.
`template:project:header:before`                                 | Project filters (before).
`template:project:header:after`                                  | Project filters (after).
`template:project:integrations`                                  | Integration page in project settings.
`template:project:creation:form`                                 | Project creation form.
`template:project:edit:form`                                     | Project modification form.
`template:project:view:form`                                     | Project view form.
`template:project:sidebar`                                       | Sidebar in project settings.
`template:project-user:sidebar`                                  | Sidebar on project user overview page.
`template:project-list:menu:before`                              | Project list: before menu entries.
`template:project-list:menu:after`                               | Project list: after menu entries.
`template:project-overview:before-description`                   | Project overview: before description.
`template:project-overview:images:dropdown`                      | Project overview: image dropdown.
`template:project-permission:after-adduser`                      | Project permission: after user.
`template:project-header:view-switcher`                          | Project view switcher.
`template:project-header:view-switcher-before-project-overview`  | Project view switcher before overview.
`template:project-header:view-switcher-before-board-view`        | Project view switcher before board.
`template:project-header:view-switcher-before-task-list`         | Project view switcher before list.
`template:search:task:footer`                                    | Task in results: footer.
`template:task:layout:top`                                       | Task layout top (after page header).
`template:task:details:top`                                      | Task summary top.
`template:task:details:bottom`                                   | Task summary bottom.
`template:task:details:first-column`                             | Task summary first column.
`template:task:details:second-column`                            | Task summary second column.
`template:task:details:third-column`                             | Task summary third column.
`template:task:details:fourth-column`                            | Task summary fourth column.
`template:task:dropdown:before-actions`                          | Task dropdown: top of menu.
`template:task:dropdown:after-basic-actions`                     | Task dropdown: after "add subtask".
`template:task:dropdown:after-add-links`                         | Task dropdown: after "add ext. link".
`template:task:dropdown:after-add-comment`                       | Task dropdown: after "add comment".
`template:task:dropdown:after-add-attachments`                   | Task dropdown: after "add screenshot".
`template:task:dropdown:after-duplicate-task`                    | Task dropdown: after "duplicate to ...".
`template:task:dropdown:after-send-mail`                         | Task dropdown: after "send by mail".
`template:task:dropdown`                                         | Task dropdown: bottom of menu.
`template:task:sidebar:information`                              | Task sidebar: section information.
`template:task:sidebar:before-actions`                           | Task sidebar: section actions: top.
`template:task:sidebar:after-basic-actions`                      | Task sidebar: after "add subtask".
`template:task:sidebar:after-add-links`                          | Task sidebar: after "add ext. link".
`template:task:sidebar:after-add-comment`                        | Task sidebar: after "add comment".
`template:task:sidebar:after-add-attachments`                    | Task sidebar: after "add screenshot".
`template:task:sidebar:after-duplicate-task`                     | Task sidebar: after "duplicate to ...".
`template:task:sidebar:after-send-mail`                          | Task sidebar: after "send by mail".
`template:task:sidebar:actions`                                  | Task sidebar: bottom Task image dropdown.
`template:task-file:images:before-thumbnail-description`         | Task image attachment description.
`template:task:form:first-column`                                | 1st column in task form.
`template:task:form:second-column`                               | 2nd column in task form.
`template:task:form:third-column`                                | 3rd column in task form.
`template:task:form:bottom-before-buttons`                       | Before form submit/cancel buttons.
`template:task:show:top`                                         | Show task page: top.
`template:task:show:bottom`                                      | Show task page: bottom.
`template:task:show:before-description`                          | Show task page: before description.
`template:task:show:before-tasklinks`                            | Show task page: before tasklinks.
`template:task:show:before-subtasks`                             | Show task page: before subtasks.
`template:task:show:before-external-links`                       | Show task page: before external links.
`template:task:show:before-internal-links`                       | Show task page: before internal links.
`template:task:show:before-timetracking`                         | Show task page: before timetracking.
`template:task:show:before-attachments`                          | Show task page: before attachments.
`template:task:show:before-comments`                             | Show task page: before comments.
`template:subtask:form:create`                                   | Create Subtask form.
`template:subtask:form:edit`                                     | Edit Subtask form.
`template:subtask:table:header:before-timetracking`              | Subtask table header before Time Tracking.
`template:subtask:table:rows`                                    | Column on row of subtasks table.
`template:user:authentication:form`                              | "Edit authentication" form in user profile.
`template:user:create-remote:form`                               | "Create remote user" form.
`template:user:external`                                         | "External authentication" page in user profile.
`template:user:integrations`                                     | Integration page in user profile.
`template:user:sidebar:actions`                                  | Sidebar in user profile (section actions).
`template:user:sidebar:information`                              | Sidebar in user profile (section information).
`template:user:show:profile:info`                                | User profile information.
