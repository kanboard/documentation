---
title: Registering New Helpers
toc: true
menu:
    main:
        parent: Developing Plugins
---

Helper Skeleton:

```php
<?php

namespace Kanboard\Plugin\MyPlugin\Helper;

use Kanboard\Core\Base;

class MyHelper extends Base
{
    public function doSomething()
    {
        return 'foobar';
    }
}
```

Register Your Helper Class:

```php
$this->helper->register('myHelper', '\Kanboard\Plugin\MyPlugin\Helper\MyHelper');
```

Using Your Helper in a Template:

```php
<p>
    <?= $this->myHelper->doSomething() ?>
</p>
```

Using Your Helper in Another Class:

```php
$this->helper->myHelper->doSomething();
```
