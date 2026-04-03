---
title: Custom Forms
toc: true
menu:
    main:
        parent: Developing Plugins
---

Adding modal forms in your plugin
---------------------------------

### Opening a modal form from a template

Using the `Kanboard\Helper\ModalHelper` class, you can open contextual menus (modals) to perform additional actions then redirect to a specific. For example from your template, for a `myform` action in your plugin's controller:

```php
<?= $this->modal->small('font-awesome-icon', 'My Form text', 'MyController', 'myform', array('plugin' => 'myplugin')) ?>
```

If you'd like your modal to redirect to the current page after submission, don't forget to give it additional params to generate the redirection. For example, adding the task's ID to redirect to the task view:

```php
<?= $this->modal->small('font-awesome-icon', 'My Form text', 'MyController', 'myform', array('plugin' => 'myplugin', 'task_id' => $task['id'])) ?>
```

### Displaying the form

Using the `Kanboard\Helper\FormHelper` class, you can generate your form, automatically handling submitted values and validation errors:

```php
<form method="post" action="<?= $this->url->href('MyController', 'myform', array('plugin' => 'myplugin', 'task_id' => $task_id)) ?>" autocomplete="off">
    <?= $this->form->csrf() ?>
    <?= $this->form->label('Single line field', 'first_field') ?>
    <?= $this->form->text('first_field', $values, $errors) ?>
    <br>
    <?= $this->form->label('Text area field', 'second_field') ?>
    <?= $this->form->textarea('second_field', $values, $errors) ?>
    <?= $this->modal->submitButtons() ?>
</form>
```

Do not add a second form in the same modal. Only [one form per modal is supported](https://github.com/kanboard/kanboard/issues/5695). If you need to handle several forms from your modal, simply open a new modal from the current modal, like so:

```php
<h2>Select a project:</h2>
<form method="post" action="<?= $this->url->href('MyController', 'myform', array('plugin' => 'myplugin', 'task_id' => $task_id)) ?>" autocomplete="off">
    <?= $this->form->csrf() ?>
    <?= $this->form->select('project_id', $projects, $values, $errors) ?>
    <?= $this->modal->submitButtons() ?>
</form>
Or alternatively, create a new one:
<?= $this->modal->small('plus', 'Create project', 'MyController', 'createproject', array('plugin' => 'myplugin', 'task_id' => $task_id)) ?></b>
```

Clicking the `Create project` link will close the current modal and open a new one with the `createproject` action, avoiding confusion between forms.

### Validating the form

To check if the request is a fresh form, or contains submitted values, you can use `$this->request->isPost()`. After validating the submitted values in `$this->request->getValues()`, you should indicate success and redirect somewhere:

```php
$this->flash->success('My form was successful');
$this->response->redirect($this->helper->url->to('TaskViewController', 'show', array('task_id' => $this->request->getStringParam('task_id'))), true);
```

Or upon error, redisplay the current form with the `$errors` and `$values` arrays in the template context:

```php
$this->flash->failure('My form failed');
$this->response->html($this->template->render('myplugin:myform', array(
    'task_id' => $task_id,
    'errors' => $errors,
    'values' => $values,
)));
```

Whether you're performing manual form validation, or using custom validators, the form helpers will display the errors alongside the erroneous submitted fields. For this purpose, make sure `errors` has one entry for each errored field, containing an array of error messages. For example:

```php
$errors = [ "age" => [ "Age cannot be a negative number" ] ];
```
