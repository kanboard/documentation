Markdown Syntax
================

Kanboard use the `Markdown
syntax <http://en.wikipedia.org/wiki/Markdown>`__ for comments or task
descriptions. Here are some examples:

Bold and italic
---------------

-  Bold text: Use 2 asterisks or 2 underscores
-  Italic text: Use 1 asterisk or 1 underscore

Source
~~~~~~

::

    This **word** is very __important__.

    And here, an *italic* word with one _underscore_.

Result
~~~~~~

This **word** is very **important**.

And here, an *italic* word with one *underscore*.

Unordered Lists
---------------

Unordered list can use asterisks, minuses or pluses.

.. _source-1:

Source
~~~~~~

::

    - Item 1
    - Item 2
    - Item 3

    or

    * Item 1
    * Item 2
    * Item 3

.. _result-1:

Result
~~~~~~

-  Item 1
-  Item 2
-  Item 3

Ordered lists
-------------

Ordered lists are prefixed by a number like that:

.. _source-2:

Source
~~~~~~

::

    1. Do that first
    2. Do this
    3. And that

.. _result-2:

Result
~~~~~~

1. Do that first
2. Do this
3. And that

Links
-----

.. _source-3:

Source
~~~~~~

::

    [My link title](https://kanboard.org/)

    <https://kanboard.org>

.. _result-3:

Result
~~~~~~

`My link title <https://kanboard.org/>`__

https://kanboard.org

Source code
-----------

Inline code
~~~~~~~~~~~

Use a backtick.

::

    Execute this command: `tail -f /var/log/messages`.

.. _result-4:

Result
~~~~~~

Execute this command: ``tail -f /var/log/messages``.

Code blocks
~~~~~~~~~~~

Use 3 backticks with eventually the language name.

.. raw:: html

   <pre>
   <code class="language-markdown">```php
   &lt;?php

   phpinfo();

   ?&gt;
   ```
   </code>
   </pre>

.. _result-5:

Result
~~~~~~

::

    <?php

    phpinfo();

    ?>

Titles
------

.. _source-4:

Source
~~~~~~

::

    # Title level 1

    ## Title level 2

    ### Title level 3
