Installation on Ubuntu
======================

Ubuntu Focal Fossa 20.04 LTS
-----------------------

Install Apache and PHP:

.. code:: bash

    sudo apt update
    sudo apt install -y apache2 libapache2-mod-php php-cli php-mbstring php-sqlite3 php-opcache php-json php-mysql php-pgsql php-ldap php-gd php-xml
    
(or) Install Nginx and PHP:

.. code:: bash

    sudo apt update
    sudo apt install nginx php-fpm php-mysql php-pgsql php-gd php-mbstring php-sqlite3 php-xml

Install Kanboard:

.. code:: bash

    #adapt version number
    version=1.2.24

    # Download the latest release from https://github.com/kanboard/kanboard/releases
    wget https://github.com/kanboard/kanboard/archive/v$version.tar.gz
    tar xzvf v$version.tar.gz -C /var/www/html/
    chown -R www-data:www-data /var/www/html/kanboard-$version/data
    
    rm v$version.tar.gz

.. note::

    - You might need to enable PHP extensions with the command ``phpenmod``.
    - Some features of Kanboard requires that you run a daily background job.

    

Ubuntu Bionic 18.04 LTS
-----------------------

Install Apache and PHP:

.. code:: bash

    sudo apt-get update
    sudo apt-get install -y apache2 libapache2-mod-php7.2 php7.2-cli php7.2-mbstring php7.2-sqlite3 \
        php7.2-opcache php7.2-json php7.2-mysql php7.2-pgsql php7.2-ldap php7.2-gd php7.2-xml

(or) Install Nginx and PHP:

.. code:: bash

    sudo apt-get update
    sudo apt-get install nginx php7.2-fpm php7.2-mysql php7.2-pgsql php7.2-gd php7.2-mbstring php7.2-sqlite3 \
        php7.2-xml

Install Kanboard:

.. code:: bash

    cd /var/www/html

    # Download the latest release from https://github.com/kanboard/kanboard/releases
    wget https://github.com/kanboard/kanboard/archive/v<version>.zip

    unzip kanboard-<version>.zip
    chown -R www-data:www-data kanboard-<version>/data
    rm kanboard-<version>.zip

.. note::

    - You might need to enable PHP extensions with the command ``phpenmod``.
    - Some features of Kanboard requires that you run a daily background job.
