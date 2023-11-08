---
title: Markdown Syntax
toc: true
menu:
    main:
        parent: Using Kanboard
---

Kanboard use the [Markdown syntax](http://en.wikipedia.org/wiki/Markdown) for comments or task descriptions.

Bold and italic
---------------

- Bold text: Use 2 asterisks or 2 underscores
- Italic text: Use 1 asterisk or 1 underscore

```markdown
This **word** is very __important__.

And here, an *italic* word with one _underscore_.
```

Unordered Lists
---------------

Unordered list can use asterisks, minuses or pluses.

```markdown
- Item 1
- Item 2
- Item 3
```

or

```markdown
* Item 1
* Item 2
* Item 3
```

Ordered lists
-------------

Ordered lists are prefixed by a number like that:

```markdown
1. Do that first
2. Do this
3. And that
```

Links
-----

```markdown
[My link title](https://kanboard.org/)

<https://kanboard.org>
```

Images
-----
```markdown
![Kanboard Icon](https://kanboard.org/assets/img/favicon.png)

or without alternative text :

![](https://kanboard.org/assets/img/favicon.png)
```

Source code
-----------

### Inline code

Use a backtick.

```markdown
Execute this command: `tail -f /var/log/messages`.
```

### Code blocks

Use 3 backticks with eventually the language name.

    ```php
    <?php

    phpinfo();

    ?>
    ```

Titles
------

```markdown
# Title level 1

## Title level 2

### Title level 3
```

Tables
------

```markdown
| Header 1  | Header 2 |
| --------- |--------- |
| a         | b        |
| c         | d        |
```

There must be at least 3 dashes separating each header cell. The outer pipes (`|`) are optional, and you don't need to make the raw Markdown line up prettily.
