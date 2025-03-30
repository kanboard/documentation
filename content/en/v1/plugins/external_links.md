---
title: External Link Providers
toc: true
menu:
    main:
        parent: Developing Plugins
---

This functionality allows you to link a task to additional items stored in another system.

For example, you can link a task to:

- A traditional web page
- An attachment (e.g., PDF documents stored on the web, archives, etc.)
- Any ticketing system (e.g., bug tracker, customer support ticket)

Each item has a type, a URL, a dependency type, and a title.

By default, Kanboard includes two types of providers:

- **Web Link**: You copy and paste a link, and Kanboard will automatically fetch the page title.
- **Attachment**: Links to anything that is not a web page.

## Workflow

1. The end-user copies and pastes the URL into the form and submits it.
2. If the link type is set to "auto," Kanboard will loop through all registered providers until a match is found.
3. The link provider then returns an object that implements the `ExternalLinkInterface`.
4. A form is displayed to the user with all pre-filled data before saving the link.

## Interfaces

To implement a new link provider in a plugin, you need to create two classes that implement the following interfaces:

- `Kanboard\Core\ExternalLink\ExternalLinkProviderInterface`
- `Kanboard\Core\ExternalLink\ExternalLinkInterface`

### ExternalLinkProviderInterface

| Method                      | Usage                                                                 |
|-----------------------------|----------------------------------------------------------------------|
| `getName()`                 | Returns the provider name (label).                                  |
| `getType()`                 | Returns the link type (saved in the database).                      |
| `getDependencies()`         | Returns a dictionary of supported dependency types for the provider.|
| `setUserTextInput($input)`  | Sets the text entered by the user.                                  |
| `match()`                   | Returns `true` if the provider can correctly parse the user input.  |
| `getLink()`                 | Returns the link with its properties.                              |

### ExternalLinkInterface

| Method            | Usage                 |
|-------------------|-----------------------|
| `getTitle()`      | Returns the link title. |
| `getUrl()`        | Returns the link URL.   |
| `setUrl($url)`    | Sets the link URL.      |

## Register a New Link Provider

In your `Plugin.php`, call the `register()` method from the `ExternalLinkManager` object:

```php
<?php

namespace Kanboard\Plugin\MyExternalLink;

use Kanboard\Core\Plugin\Base;

class Plugin extends Base
{
    public function initialize()
    {
        $this->externalLinkManager->register(new MyLinkProvider($this->container));
    }
}
```

## Examples

- Kanboard includes the default providers "WebLink" and "Attachment."
