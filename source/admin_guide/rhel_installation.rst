Installation on RedHat/Centos/Oracle Linux Enterprise
=====================================================

.. warning::

    This page hasn't been updated for a while, and it's probably obsolete.


Centos 7
--------

Install PHP and Apache:

.. code:: bash

    yum install -y php php-xml php-mbstring php-pdo php-gd unzip wget

By default, Centos 7 use PHP 5.4.16 and Apache 2.4.6.

Restart Apache:

.. code:: bash

    systemctl restart httpd.service

Install Kanboard:

.. code:: bash

    cd /var/www/html

    # Download the latest release from https://github.com/kanboard/kanboard/releases
    wget https://github.com/kanboard/kanboard/archive/v<version>.zip

    unzip kanboard-<version>.zip
    chown -R apache:apache kanboard-<version>/data
    rm kanboard-<version>.zip

SELinux restrictions
--------------------

If SELinux is enabled, be sure that the Apache user can write to the
directory data:

.. code:: bash

    chcon -R -t httpd_sys_content_rw_t /var/www/html/kanboard/data

Be sure to configure your server to allow Kanboard to send emails and
make external network requests, for example with SELinux:

.. code:: bash

    setsebool -P httpd_can_network_connect=1

Allowing external connections is necessary if you use LDAP, SMTP, Web
hooks or any third-party integration.
