Running Kanboard with Docker
============================

Kanboard can run easily with `Docker <https://www.docker.com>`_.

Docker Tags
-----------

+--------------+-------------------------------------------------------+
| Tag          | Description                                           |
+==============+=======================================================+
| latest       | Latest stable release                                 |
+--------------+-------------------------------------------------------+
| v1.2.x       | Specific version of Kanboard                          |
+--------------+-------------------------------------------------------+
| master       | Latest development changes (master branch)            |
+--------------+-------------------------------------------------------+

Environment Variables
---------------------

+-----------+----------------------------------------------------------+
| Variable  | Description                                              |
+===========+==========================================================+
| DATABASE\_| ``[database type]://[username]:[password]@[host]:[port]/ |
| URL       | [database name]``,                                       |
|           | example: ``postgres://foo:foo@myserver:5432/kanboard``   |
+-----------+----------------------------------------------------------+
| DEBUG     | Enable/Disable debug mode: ``true`` or ``false``         |
+-----------+----------------------------------------------------------+
| API_AUTHE | Custom API token                                         |
| NTICATION |                                                          |
| _TOKEN    |                                                          |
+-----------+----------------------------------------------------------+

Volumes
-------

+-------------------------+-------------------------------------------------------+
| Path                    | Description                                           |
+=========================+=======================================================+
| /var/www/app/data       | Application data (Sqlite database, attachments, etc.) |
+-------------------------+-------------------------------------------------------+
| /var/www/app/plugins    | Plugins                                               |
+-------------------------+-------------------------------------------------------+
| /etc/nginx/ssl          | SSL certificates                                      |
+-------------------------+-------------------------------------------------------+

Custom Config File
------------------

- The container already include a custom config file located at ``/var/www/app/config.php``.
- You can store your own config file on the data volume: ``/var/www/app/data/config.php``.
- You must restart the container to take into account the new parameters of your custom config file.

Running the Container
---------------------

Basic Usage
~~~~~~~~~~~

.. code:: bash

    docker pull kanboard/kanboard:v1.2.5
    docker run -d --name kanboard -p 80:80 -t kanboard/kanboard:v1.2.5

Docker Compose
~~~~~~~~~~~~~~

There is a ``docker-compose.yml`` file in Kanboard repository. Here an example:

.. code::

    version: '2'
    services:
      kanboard:
        image: kanboard/kanboard:latest
        ports:
          - "80:80"
          - "443:443"
        volumes:
          - kanboard_data:/var/www/app/data
          - kanboard_plugins:/var/www/app/plugins
          - kanboard_ssl:/etc/nginx/ssl
    volumes:
      kanboard_data:
        driver: local
      kanboard_plugins:
        driver: local
      kanboard_ssl:
        driver: local

Starting the container with Docker Compose:

.. code:: bash

    docker-compose up

Build Your Own Docker Image
---------------------------

Clone the Kanboard repository and run the following command:

.. code:: bash

    make docker-image

.. note::

    - `Official Kanboard images <https://hub.docker.com/r/kanboard/kanboard/>`__
    - `Docker documentation <https://docs.docker.com/>`__
    - Since Kanboard > v1.1.0, the tag "stable" is not used anymore
    - Since Kanboard > v1.2.5, the tag "latest" point to the latest stable release instead of the master branch
    - To send emails, you must use the SMTP method or a plugin like Mailgun/Sendgrid/Postmark
