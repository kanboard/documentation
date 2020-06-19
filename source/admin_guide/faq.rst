Frequently Asked Questions
==========================

Can you recommend a web hosting provider for Kanboard?
------------------------------------------------------

Kanboard works well with any great VPS hosting provider such as `Digital
Ocean <https://www.digitalocean.com/?refcode=4b541f47aae4>`__,
`Linode <https://www.linode.com/?r=4e381ac8a61116f40c60dc7438acc719610d8b11>`__
or `Gandi <https://www.gandi.net/>`__.

To have the best performances, choose a provider with fast disk I/O
because Kanboard use Sqlite by default. Avoid hosting providers that use
a shared NFS mount point.

.. note:: Using a shared hosting provider is not recommended. Use your own server.

How to display a link to the task in notifications?
---------------------------------------------------

To do that, you have to specify the URL of your Kanboard installation in
your Application Settings.
By default, nothing is defined, so no links will be displayed.

Examples:

-  http://myserver/kanboard/
-  http://kanboard.mydomain.com/

Don’t forget the ending slash ``/``.

You need to define that manually because Kanboard cannot guess the URL
from a command line script and some people have a very specific
configuration.

I have the error “There is no suitable CSPRNG installed on your system”
-----------------------------------------------------------------------

If you use PHP < 7.0, you need to have the openssl extension enabled or
``/dev/urandom`` accessible from the application if restricted by an
``open_basedir`` restriction.

Page not found and the URL seems wrong (&amp;)
----------------------------------------------

-  The URL looks like
   ``/?controller=auth&amp;action=login&amp;redirect_query=`` instead of
   ``?controller=auth&action=login&redirect_query=``
-  Kanboard returns a “Page not found” error

This issue comes from your PHP configuration, the value of
``arg_separator.output`` is not the PHP’s default, there is different
ways to fix that:

Change the value directly in your ``php.ini`` if you can:

::

    arg_separator.output = "&"

Override the value with a ``.htaccess``:

::

    php_value arg_separator.output "&"

Otherwise Kanboard will try to override the value directly in PHP.

Authentication failure with the API and Apache + PHP-FPM
--------------------------------------------------------

php-cgi under Apache does not pass HTTP Basic user/pass to PHP by
default. For this workaround to work, add these lines to your
``.htaccess`` file:

::

    RewriteCond %{HTTP:Authorization} ^(.+)$
    RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]

How to test Kanboard with the PHP built-in web server?
------------------------------------------------------

If you don’t want to install a web server like Apache on localhost. You
can test with the `embedded web server of
PHP <http://www.php.net/manual/en/features.commandline.webserver.php>`__:

.. code:: bash

    unzip kanboard-VERSION.zip
    cd kanboard
    php -S localhost:8000
    open http://localhost:8000/

I get a blank page after installing or upgrading Kanboard
---------------------------------------------------------

-  Check if you have installed all requirements on your server
-  Check the PHP and Apache error logs
-  Check if the files have the correct permissions
-  If you use an aggressive OPcode caching, reload your web-server or
   php-fpm

Solving Database Migration Issues
---------------------------------

-  SQL migrations are executed automatically when you upgrade Kanboard
   to a new version
-  For Postgres and Mysql, the current schema version number is stored
   in the table ``schema_version`` and for Sqlite this is stored in the
   variable ``user_version``
-  Migrations are defined in the file ``app/Schema/<DatabaseType>.php``
-  Each function is a migration
-  Each migration is executed in a transaction
-  If migration generate an error, a rollback is performed

When upgrading:

-  Always backup your data
-  Do not run migrations in parallel from multiple processes

If you got the error “Unable to run SQL migrations […]”, here are the
steps to fix it manually:

1. Open the file corresponding to your database
   ``app/Schema/Sqlite.php`` or ``app/Schema/Mysql.php``
2. Go to the failed migration function
3. Execute manually the SQL queries defined in the function
4. If you encounter an error, report the issue to the bug tracker with
   the exact SQL error
5. When all SQL statements of the migration are executed, update the
   schema version number
6. Run other migrations

I’m not able to login with Internet Explorer and Microsoft IIS
--------------------------------------------------------------

If you are not able to login and always get the error **“Username or
password required”** even if you have entered the right credentials,
that means there is a problem with the session.

For example, this is a known issue if you meet these criteria:

-  You are using a domain name with an underscore:
   ``kanboard_something.mycompany.tld``
-  You are using Microsoft Windows Server and IIS
-  Your browser is Internet Explorer

Solution: **Do not use underscore in the domain name because this is not
a valid domain name**.

Explanation: Internet Explorer doesn’t accept cookies with a domain name
with underscores because it’s not valid.

Reference:

-  https://support.microsoft.com/en-us/kb/316112

How to change attachment size limit?
------------------------------------

The file upload size is not defined by Kanboard itself but by PHP and your webserver.

In your ``php.ini``, change the following lines:

.. code:: 

    # Set size limit to 20MB
    upload_max_filesize = 20M
    post_max_size = 20M

If you use Nginx, define this value:

.. code::

    client_max_body_size 20M;

See `<http://nginx.org/en/docs/http/ngx_http_core_module.html#client_max_body_size>`_.

Is it possible to customize table names prefix?
-----------------------------------------------

Short answer: No.

- Kanboard is designed to use its own database.
- Changing existing code will require too many changes.
- Mixing multiple software into the same database is a bad practice (shared hosting providers are not recommended).

Why there is no official native mobile application?
---------------------------------------------------

The development of a native mobile application is let to the community.

- Developing a native mobile application for each platform (iOS/Android) for each device type (Smartphone/Tablet) require a lot of work and money.
- That require different skill set than developing a web application.
- To develop a quality application, you have to use the official SDK of each platform. So, you end up developing twice the same application.
- Publishing a mobile application on a store (App Store/Play Store) is not free, you have to pay, even if your software is free.
- The web user interface is responsive, this is not prefect but that allows you to quickly check something.
- This is not really practical to use the board on a tiny screen.
