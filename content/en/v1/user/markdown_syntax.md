---
title: Markdown Syntax
toc: true
menu:
    main:
        parent: Using Kanboard
---

Kanboard uses the [Markdown syntax](http://en.wikipedia.org/wiki/Markdown) for comments and task descriptions.

Bold and Italic
---------------

- Bold text: Use 2 asterisks or 2 underscores.
- Italic text: Use 1 asterisk or 1 underscore.

```markdown
This **word** is very __important__.

And here, an *italic* word with one _underscore_.
```

Unordered Lists
---------------

Unordered lists can use asterisks, minuses, or pluses.

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

Ordered Lists
-------------

Ordered lists are prefixed by a number, like this:

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
------

```markdown
![Kanboard Icon](https://kanboard.org/assets/img/favicon.png)

or without alternative text:

![](https://kanboard.org/assets/img/favicon.png)
```

Source Code
-----------

### Inline Code

Use a backtick.

```markdown
Execute this command: `tail -f /var/log/messages`.
```

### Code Blocks

Use 3 backticks, optionally with the language name.


    ```php
    <?php

    phpinfo();

    ?>
    ```

Titles
------

```markdown
# Title Level 1

## Title Level 2

### Title Level 3
```

Tables
------

```markdown
| Header 1  | Header 2 |
| --------- | -------- |
| a         | b        |
| c         | d        |
```

There must be at least 3 dashes separating each header cell. The outer pipes (`|`) are optional, and you don't need to make the raw Markdown line up prettily.
