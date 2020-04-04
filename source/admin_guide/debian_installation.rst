Installation on Debian
======================

Debian 10 (Buster)
------------------

Install Apache and PHP:

.. code:: bash

    apt update
    apt install -y apache2 libapache2-mod-php php-cli php-mbstring \
        php-sqlite3 php-opcache php-json php-ldap php-gd php-xml  \
        php-mysql php-pgsql

    systemctl enable apache2

Install Kanboard:

.. code:: bash

    version=1.2.13
    wget https://github.com/kanboard/kanboard/archive/v$version.tar.gz
    tar xzvf v$version.tar.gz -C /var/www/html/
    chown -R www-data:www-data /var/www/html/kanboard-$version/data

Debian 9 (Stretch)
------------------

Install Apache and PHP:

.. code:: bash

    apt update
    apt install -y apache2 libapache2-mod-php7.0 php7.0-cli php7.0-mbstring \
        php7.0-sqlite3 php7.0-opcache php7.0-json php7.0-mysql php7.0-pgsql \
        php7.0-ldap php7.0-gd php7.0-xml

    systemctl enable apache2

Install Kanboard:

.. code:: bash

    version=1.2.5
    wget https://github.com/kanboard/kanboard/archive/v$version.tar.gz
    tar xzvf v$version.tar.gz -C /var/www/
    chown -R www-data:www-data /var/www/kanboard-$version/data

Debian 8 (Jessie)
-----------------

.. warning:: Debian 8 ships with PHP 5.  Since version 1.2.13, Kanboard requires at least PHP 7.2.

Install Apache and PHP:

.. code:: bash

    apt-get update
    apt-get install -y php5 php5-sqlite php5-gd unzip
    service apache2 restart

Install Kanboard:

.. code:: bash

    cd /var/www/html

    # Download the latest release from https://github.com/kanboard/kanboard/releases
    wget https://github.com/kanboard/kanboard/archive/v<version>.zip

    unzip kanboard-<version>.zip
    chown -R www-data:www-data kanboard-<version>/data
    rm kanboard-<version>.zip
