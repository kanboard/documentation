Markdown Syntax
================

Kanboard use the `Markdown
syntax <http://en.wikipedia.org/wiki/Markdown>`__ for comments or task
descriptions.

Line Breaks
-----------

Two spaces after the last world will render the text on a new line:

::

    Hello  (<-- two spaces)
    World

::

    Hello
    World

A blank line will produces the same effect:

::

    Hello

    World

::

    Hello
    World

Using no blank line or no spaces at the end will render the text on the same line:

::

    Hello
    World

::

    HelloWorld

Bold and italic
---------------

-  Bold text: Use 2 asterisks or 2 underscores
-  Italic text: Use 1 asterisk or 1 underscore

::

    This **word** is very __important__.

    And here, an *italic* word with one _underscore_.

Unordered Lists
---------------

Unordered list can use asterisks, minuses or pluses.

::

    - Item 1
    - Item 2
    - Item 3

    or

    * Item 1
    * Item 2
    * Item 3

Ordered lists
-------------

Ordered lists are prefixed by a number like that:

::

    1. Do that first
    2. Do this
    3. And that

Links
-----

::

    [My link title](https://kanboard.org/)

    <https://kanboard.org>

Source code
-----------

Inline code
~~~~~~~~~~~

Use a backtick.

::

    Execute this command: `tail -f /var/log/messages`.

Code blocks
~~~~~~~~~~~

Use 3 backticks with eventually the language name.

::

    ```php
    <?php

    phpinfo();

    ?>
    ```

Titles
------

::

    # Title level 1

    ## Title level 2

    ### Title level 3

Tables
------

::

    | Header 1  | Header 2 |
    | --------- |--------- |
    | a         | b        |
    | c         | d        |

There must be at least 3 dashes separating each header cell.
The outer pipes (|) are optional, and you don't need to make the
raw Markdown line up prettily.
