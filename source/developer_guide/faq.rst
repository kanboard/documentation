Frequently Asked Questions
==========================

Why are you not developing my feature request?
----------------------------------------------

Kanboard is an open source project with limited resources.

- Developing and maintaining a software takes a lot of time.
- Do not under estimate the complexity of introducing changes.
- This is a free and open source project, no one owes you anything.
- If you miss something, contribute to the project.
- Do not expect anyone to work for free.
- People are not going to spend days and weeks of their time to develop a feature just for you.
- No one manages projects in the same way, this is not possible to satisfy the workflow of everyone.
- The number of features is voluntarily limited. Nobody likes bloatware.
- Improving existing features is more important than adding new ones.

Why do you close inactive issues automatically?
-----------------------------------------------

- If nobody manifested any interest to develop your feature request, then there is no point of keeping it open.
- Keeping issues open indefinitely will not get fixed by itself.
- Stale issues create more noise.

Why did you close my question on the bug tracker?
-------------------------------------------------

- The bug tracker should be reserved only for bug reports.
- Bug triage takes a lot of time.
- If you have a question or if you need help, go to the `forum <https://kanboard.discourse.group/>`_.

.. _bug-report:

How to make a bug report?
-------------------------

You should make sure that you give all information to be able to reproduce the problem.

1. Check for duplicates before creating a new issue.
2. Write in English even if you don't speak English.
3. Describe your environment:
    - Operating System
    - Browser
    - Database
    - Version of PHP
    - Version of Kanboard
4. Describe the actual behavior:
    - Add screenshots
    - Attach log files
    - Avoid ambiguity, be explicit
5. List all the steps to reproduce the problem.
6. Describe what you expect.

.. note::  Do not ask questions on the bug tracker, use the `forum <https://kanboard.discourse.group/>`_.

How to add a new plugin to the website?
---------------------------------------

Follow these instructions: `<https://github.com/kanboard/website#how-to-add-a-new-plugin-to-the-list>`_

.. _update-docs:

How to update this documentation?
---------------------------------

- The documentation source code is available here: `<https://github.com/kanboard/documentation>`_.
- We use `Sphinx <http://www.sphinx-doc.org/>`_ and the `reStructuredText <https://en.wikipedia.org/wiki/ReStructuredText>`_  markup language to generate this documentation in multiple formats.
- To update this documentation, send a pull-request to the project mentioned above.

How to translate the documentation?
-----------------------------------

Each language has its own repository:

- `Czech <https://github.com/kanboard/documentation-cz>`_
- `French <https://github.com/kanboard/documentation-fr>`_
- `Portuguese <https://github.com/kanboard/documentation-pt>`_
- `Russian <https://github.com/kanboard/documentation-ru>`_
- `Spanish <https://github.com/kanboard/documentation-es>`_
- `Turkish <https://github.com/kanboard/documentation-tr>`_

To update a translation, send a pull-request to the corresponding project.
The directory layout and the file names must be the same as the english version.

If you would like to create a new translation, follow these steps:

- Create a new repository
- Run ``sphinx-quickstart``
- Translate the documents
- Push your changes to GitHub
- Contact the maintainers on the forum to add your translation to the list

Why minified files are committed into the source tree?
------------------------------------------------------

- This is to simplify Kanboard release process.
- People can download the archive directly from GitHub.
- Occasional contributors can checkout the source code and work on a patch without having to worry about all Javascript dependencies.

Why PHP vendor directory is committed into the source tree?
-----------------------------------------------------------

- This is to simplify Kanboard release process.
- People can download the archive directly from GitHub.
- Occasional contributors can checkout the source code and work on a patch without having to worry about all Composer dependencies.
