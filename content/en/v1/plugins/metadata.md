---
title: Metadata
toc: true
menu:
    main:
        parent: Developing Plugins
---

You can attach metadata to each project, task, user, or the entire application. Metadata are custom fields stored in a key/value table.

For example, your plugin can store external information for a task or new settings for a project. This allows you to extend the default fields without creating new tables.

Attach metadata to tasks and remove them
----------------------------------------

```php
// Return a dictionary of metadata (keys/values) for the $task_id
$this->taskMetadataModel->getAll($task_id);

// Get a specific value for a task
$this->taskMetadataModel->get($task_id, 'my_plugin_variable', 'default_value');

// Return true if the metadata 'my_plugin_variable' exists
$this->taskMetadataModel->exists($task_id, 'my_plugin_variable');

// Create or update metadata for the task
$this->taskMetadataModel->save($task_id, ['my_plugin_variable' => 'something']);

// Remove metadata from a project
$this->projectMetadataModel->remove($project_id, 'my_plugin_variable');
```

Metadata types
--------------

- TaskMetadata: `$this->taskMetadataModel`
- ProjectMetadata: `$this->projectMetadataModel`
- UserMetadata: `$this->userMetadataModel`
- Settings/Config: `$this->configModel`

{{< hint type="info" >}}
Always prefix metadata names with your plugin name.
{{</ hint >}}
