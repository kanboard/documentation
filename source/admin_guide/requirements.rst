Requirements
============

.. _requirements:

Server Side
-----------

Compatible Operating Systems
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-------------------------------------+
| Operating System                    |
+=====================================+
| Alpine Linux                        |
+-------------------------------------+
| Linux Ubuntu                        |
+-------------------------------------+
| Linux Centos                        |
+-------------------------------------+
| Linux Redhat                        |
+-------------------------------------+
| Linux Debian                        |
+-------------------------------------+
| FreeBSD                             |
+-------------------------------------+
| Microsoft Windows                   |
+-------------------------------------+

.. note:: The recommended operating system is GNU/Linux (Debian/Ubuntu/RHEL/Alpine Linux).

Compatible Databases
~~~~~~~~~~~~~~~~~~~~

+-------------------+
| Database          |
+===================+
| Sqlite >= 3.7     |
+-------------------+
| Mysql >= 5.6      |
+-------------------+
| MariaDB >= 10     |
+-------------------+
| Postgresql >= 9.4 |
+-------------------+

Which database to choose?

+----------------+---------------------------------------------------+
| Type           | Usage                                             |
+================+===================================================+
| Sqlite         | Single user or small team (almost no concurrency) |
+----------------+---------------------------------------------------+
| Mysql/Postgres | Larger team, high-availability configuration      |
+----------------+---------------------------------------------------+

.. note::

    - The recommended database is Postgresql.
    - Do not use Sqlite with NFS.

Compatible Web Servers
~~~~~~~~~~~~~~~~~~~~~~

+--------------------+
| Web Server         |
+====================+
| Apache HTTP Server |
+--------------------+
| Nginx              |
+--------------------+
| Microsoft IIS      |
+--------------------+
| Caddy Server       |
+--------------------+

Kanboard is pre-configured to work with Apache (URL rewriting).

.. warning::

    -  Kanboard is NOT compatible with Apache ``mod_security``.
    -  If you use Apache, you must have the module ``mod_version``.

PHP Versions
~~~~~~~~~~~~

+--------------+
| PHP Version  |
+==============+
| PHP >= 7.4   |
+--------------+

.. note::

    - Since version 1.2.22, Kanboard requires at least PHP 7.4
    - Since version 1.2.13, Kanboard requires at least PHP 7.2
    - The latest version of PHP is recommended.

PHP Extensions Required
~~~~~~~~~~~~~~~~~~~~~~~

+---------------+-------------------------------+
| PHP Extension | Note                          |
+===============+===============================+
| pdo_sqlite    | Only if you use Sqlite        |
+---------------+-------------------------------+
| pdo_mysql     | Only if you use Mysql/MariaDB |
+---------------+-------------------------------+
| pdo_pgsql     | Only if you use Postgres      |
+---------------+-------------------------------+
| gd            |                               |
+---------------+-------------------------------+
| mbstring      |                               |
+---------------+-------------------------------+
| openssl       |                               |
+---------------+-------------------------------+
| json          |                               |
+---------------+-------------------------------+
| hash          |                               |
+---------------+-------------------------------+
| ctype         |                               |
+---------------+-------------------------------+
| session       |                               |
+---------------+-------------------------------+
| filter        |                               |
+---------------+-------------------------------+
| xml           |                               |
+---------------+-------------------------------+
| SimpleXML     |                               |
+---------------+-------------------------------+
| dom           |                               |
+---------------+-------------------------------+

Optional PHP extensions
~~~~~~~~~~~~~~~~~~~~~~~

+---------------+---------------------------------------+
| PHP Extension | Note                                  |
+===============+=======================================+
| zip           | Used to install plugins from web ui   |
+---------------+---------------------------------------+
| ldap          | Only for LDAP integration             |
+---------------+---------------------------------------+
| curl          | Use cURL as HTTP client               |
+---------------+---------------------------------------+

Recommendations
~~~~~~~~~~~~~~~

-  Modern Linux or Unix operating system with the latest version of PHP.
-  Best performances are obtained with the latest version of PHP with
   OpCode caching activated.

Client side
-----------

Browsers
~~~~~~~~

Always use a modern browser with the latest version if possible:

+-----------------------------------+
| Browser                           |
+===================================+
| Safari                            |
+-----------------------------------+
| Google Chrome                     |
+-----------------------------------+
| Mozilla Firefox                   |
+-----------------------------------+
| Microsoft Edge                    |
+-----------------------------------+

.. note:: The recommended browsers are Mozilla Firefox or Google Chrome.

.. warning:: Microsoft Internet Explorer is not supported since version 1.2.11

Devices
~~~~~~~

+-------------------+-------------------+
| Device            | Screen resolution |
+===================+===================+
| Laptop or desktop | >= 1366 x 768     |
+-------------------+-------------------+
| Tablet            | >= 1024 x 768     |
+-------------------+-------------------+

