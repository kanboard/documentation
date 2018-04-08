Installation on Microsoft Windows Server
========================================

Windows Server and Apache
-------------------------

This guide will help you to setup step by step Kanboard on a Windows
Server with Apache and PHP.

Note: If you have a 64 bits platform choose “x64” otherwise choose “x86”
for 32-bit systems.

Visual C++ Redistributable Installation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

PHP and Apache are compiled with Visual Studio so you need to install
this library if it’s not already done.

1. Download the library from the `official Microsoft
   website <http://www.microsoft.com/en-us/download/details.aspx?id=30679>`__
2. Run the installer ``vcredist_x64.exe`` or ``vcredist_x86.exe``
   according to your platform

Apache Installation
~~~~~~~~~~~~~~~~~~~

1. Download Apache binary from `Apache
   Lounge <http://www.apachelounge.com/download/>`__
2. Unzip the Apache24 folder to ``C:\Apache24``

Define the server name:

Open the file ``C:\Apache24\conf\httpd.conf`` and add the directive:

::

    ServerName localhost

Install the Apache service
~~~~~~~~~~~~~~~~~~~~~~~~~~

Open a command prompt (``cmd.exe``) and go to the directory
``C:\Apache24\bin``:

.. code:: bash

    cd C:\Apache24\bin

    # Install the windows service
    httpd.exe -k install

Install ApacheMonitor
~~~~~~~~~~~~~~~~~~~~~

-  Double click on ``C:\Apache24\bin\ApacheMonitor.exe``, or put it in
   your startup folder.
-  Right click on the icon and start Apache

Check the Apache installation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Go to http://localhost/ you should see a blank page with the text “It
works!”.

PHP installation
~~~~~~~~~~~~~~~~

1. Download the last stable version of PHP from the `official PHP
   website <http://windows.php.net/download/>`__, choose the **Thread
   Safe** version and use the exact same build type as Apache: x86 or
   x64
2. Unzip the files to ``C:\php``
3. Navigate to the PHP folder and rename the file ``php.ini-production``
   to ``php.ini``

Edit the ``php.ini``:

Uncomment extension directory:

.. code:: ini

    extension_dir = "C:/php/ext"

Uncomment these PHP modules:

.. code:: ini

    extension=php_gd2.dll
    extension=php_ldap.dll
    extension=php_mbstring.dll
    extension=php_openssl.dll
    extension=php_pdo_sqlite.dll

Set the time zone:

.. code:: ini

    date.timezone = America/Montreal

The list of supported time zones can be found in the `PHP
documentation <http://php.net/manual/en/timezones.america.php>`__.

Load the PHP module for Apache:

Add this configuration in the file ``C:\Apache24\conf\httpd.conf``:

::

    LoadModule php5_module "c:/php/php5apache2_4.dll"
    AddHandler application/x-httpd-php .php

    # configure the path to php.ini
    PHPIniDir "C:/php"

    # change this directive
    DirectoryIndex index.php index.html

Restart Apache.

Test your PHP installation:

Create a file named ``phpinfo.php`` in the folder
``C:\Apache24\htdocs``:

.. code:: php

    <?php

    phpinfo();

    ?>

Go to http://localhost/phpinfo.php and should see all information about
your PHP installation.

Kanboard installation
~~~~~~~~~~~~~~~~~~~~~

-  Download the zip file
-  Decompress the archive in ``C:\Apache24\htdocs\kanboard`` by example
-  Open your web browser to use Kanboard http://localhost/kanboard/
-  The default credentials are **admin/admin**

Windows Server and IIS
----------------------

This guide will help you to setup step by step Kanboard on a Windows
Server with IIS and PHP.

PHP Installation
~~~~~~~~~~~~~~~~

-  Install IIS on your server (Add a new role and don’t forget to enable
   CGI/FastCGI)
-  Install PHP by following the official documentation:

   -  `Microsoft IIS 5.1 and IIS
      6.0 <http://php.net/manual/en/install.windows.iis6.php>`__
   -  `Microsoft IIS 7.0 and
      later <http://php.net/manual/en/install.windows.iis7.php>`__
   -  `PHP for Windows is available
      here <http://windows.php.net/download/>`__

PHP.ini
~~~~~~~

You need at least, these extensions in your ``php.ini``:

.. code:: ini

    extension=php_gd2.dll
    extension=php_ldap.dll
    extension=php_mbstring.dll
    extension=php_openssl.dll
    extension=php_pdo_sqlite.dll

Do not forget to set the time zone:

.. code:: ini

    date.timezone = America/Montreal

The list of supported time zones can be found in the `PHP
documentation <http://php.net/manual/en/timezones.america.php>`__.

.. note::

    -  Don’t forget to enable the required php extensions mentioned above

    -  If you got an error about “the library MSVCP110.dll is missing”, you
       probably need to download the Visual C++ Redistributable for Visual
       Studio from the Microsoft website.

IIS Modules
~~~~~~~~~~~

The Kanboard archive contains a ``web.config`` file to enable URL
rewriting. This configuration require the
`Rewrite module for
IIS <http://www.iis.net/learn/extensions/url-rewrite-module/using-the-url-rewrite-module>`__.

If you don’t have the rewrite module, you will get an internal server
error (500) from IIS. If you don’t want to have Kanboard with nice URLs,
you can remove the file ``web.config``.

Kanboard installation
~~~~~~~~~~~~~~~~~~~~~

-  Download the zip file
-  Decompress the archive in ``C:\inetpub\wwwroot\kanboard`` by example
-  Make sure the directory ``data`` is writable by the IIS user
-  Open your web browser to use Kanboard http://localhost/kanboard/
-  The default credentials are **admin/admin**
