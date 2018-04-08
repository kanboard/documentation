Installation Instructions
=========================

Firstly, check the requirements before going further.

From the archive (stable version)
---------------------------------

1. You must have a web server with PHP installed
2. Download the source code and copy the directory ``kanboard`` where
   you want
3. Check if the directory ``data`` is writeable by the web server user
4. With your browser go to http://yourpersonalserver/kanboard
5. The default login and password is **admin/admin**
6. Start using the software
7. Don’t forget to change your password!

The ``data`` folder is used to store:

-  Sqlite database: ``db.sqlite``
-  Debug file: ``debug.log`` (if debug mode is enabled with the ``file``
   driver)
-  Uploaded files: ``files/*``
-  Image thumbnails: ``files/thumbnails/*``

People who are using a remote database (Mysql/Postgresql) and a remote
object storage (Aws S3 or similar) don’t necessarily need to have a
persistent local data folder or to change the permissions for the
folder.

From the git repository (development version)
---------------------------------------------

1. ``git clone https://github.com/kanboard/kanboard.git``
2. Go to the third step just above

Note: This method will install the **current development version**, use
at your own risk.

.. warning::  **Security measures:**

    -  Do not forget to change the default user/password
    -  Do not allow everybody to access to the directory ``data`` from the
       URL. A ``.htaccess`` file for Apache and a ``web.config`` file for
       IIS is included but other web servers will have to be configured
       manually.
