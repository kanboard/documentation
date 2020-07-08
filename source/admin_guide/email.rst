Email Configuration
===================

User Settings
-------------

To receive email notifications, users of Kanboard must have:

-  Activated notifications in their profile
-  Have a valid email address in their profile
-  Be a member of the project that will trigger notifications

Note: The logged user who performs the action doesn’t receive any
notifications, only other project members.

Email Transports
----------------

There are several email transports available:

-  SMTP
-  Sendmail
-  PHP native mail function
-  Other methods can be provided by external plugins: Postmark, Sendgrid
   and Mailgun

Server Settings
---------------

By default, Kanboard will use the bundled PHP mail function to send
emails. Usually that requires no configuration if your server can
already send emails.

However, it’s possible to use other methods, the SMTP protocol and
Sendmail.

SMTP Configuration
~~~~~~~~~~~~~~~~~~

Rename the file ``config.default.php`` to ``config.php`` and change
these values:

.. code:: php

    // We choose "smtp" as mail transport
    define('MAIL_TRANSPORT', 'smtp');

    // We define our server settings
    define('MAIL_SMTP_HOSTNAME', 'mail.example.com');
    define('MAIL_SMTP_PORT', 25);

    // Credentials for authentication on the SMTP server (not mandatory)
    define('MAIL_SMTP_USERNAME', 'username');
    define('MAIL_SMTP_PASSWORD', 'super password');

It’s also possible to use a secure connection, TLS or SSL:

.. code:: php

    define('MAIL_SMTP_ENCRYPTION', 'ssl'); // Valid values are "null", "ssl" or "tls"

Some servers will reject emails based on the hostname transmitted with the HELO
(EHLO) command (see RFC 5321). The (fully-qualified) hostname supplied in the
HELO command can be set explicitly by:

.. code:: php

    define('MAIL_SMTP_HELO_NAME', null); // valid: null (default), or FQDN


Sendmail Configuration
~~~~~~~~~~~~~~~~~~~~~~

By default the sendmail command will be ``/usr/sbin/sendmail -bs`` but
you can customize that in your config file.

Example:

.. code:: php

    // We choose "sendmail" as mail transport
    define('MAIL_TRANSPORT', 'sendmail');

    // If you need to change the sendmail command, replace the value
    define('MAIL_SENDMAIL_COMMAND', '/usr/sbin/sendmail -bs');

PHP built-in mail function
~~~~~~~~~~~~~~~~~~~~~~~~~~

This is the default configuration:

.. code:: php

    define('MAIL_TRANSPORT', 'mail');

Sender Email Address
~~~~~~~~~~~~~~~~~~~~

By default, emails will use the sender address
``notifications@kanboard.local``. It’s not possible to reply to this
address.

You can customize this address by changing the value of the constant
``MAIL_FROM`` in your config file.

.. code:: php

    define('MAIL_FROM', 'kanboard@mydomain.tld');

That can be useful if your SMTP server configuration doesn’t accept the
default address.

Troubleshooting
---------------

If no emails are sent and you are sure that everything is configured
correctly:

-  Check your spam folder
-  Enable the debug mode and check the debug file ``data/debug.log``,
   you should see the exact error
-  Be sure that your server or your hosting provider allows you to send
   emails
-  If you use SeLinux, allow PHP to send emails
