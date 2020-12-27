Run Kanboard with Docker
========================

.. warning:: Please, do not update the software blindly without reading the `ChangeLog <https://github.com/kanboard/kanboard/blob/master/ChangeLog>`_.
             Always check for breaking changes if any.

Docker Registries
-----------------

+----------------------------+-----------------------------------------+
| Registry                   | Description                             |
+============================+=========================================+
| Docker Hub                 | ``docker.io/kanboard/kanboard``         |
+----------------------------+-----------------------------------------+
| GitHub Container Registry  | ``ghcr.io/kanboard/kanboard``           |
+----------------------------+-----------------------------------------+

Docker Tags
-----------

+--------------+-------------------------------------------------------+
| Tag          | Description                                           |
+==============+=======================================================+
| ``latest``   | Latest stable release                                 |
+--------------+-------------------------------------------------------+
| ``nightly``  | Nightly build (latest development changes)            |
+--------------+-------------------------------------------------------+
| ``v1.2.x``   | Specific version of Kanboard                          |
+--------------+-------------------------------------------------------+

Environment Variables
---------------------

All Kanboard configuration options can be used as environment variable.

Volumes
-------

+-------------------------+-------------------------------------------------------+
| Path                    | Description                                           |
+=========================+=======================================================+
| ``/var/www/app/data``   | Application data (Sqlite database, attachments, etc.) |
+-------------------------+-------------------------------------------------------+
| ``/var/www/app/plugins``| Plugins                                               |
+-------------------------+-------------------------------------------------------+
| ``/etc/nginx/ssl``      | SSL certificates                                      |
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

    docker run -d --name kanboard -p 80:80 -t kanboard/kanboard:v1.2.8

Docker Compose
~~~~~~~~~~~~~~

There is a ``docker-compose.yml`` file in Kanboard repository. Here an example with Sqlite:

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
      kanboard_plugins:
      kanboard_ssl:

Another example with MariaDB:

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
      environment:
        DATABASE_URL: mysql://kanboard:kanboard-secret@db/kanboard
    db:
      image: mariadb:latest
      command: --default-authentication-plugin=mysql_native_password
      environment:
        MYSQL_ROOT_PASSWORD: secret
        MYSQL_DATABASE: kanboard
        MYSQL_USER: kanboard
        MYSQL_PASSWORD: kanboard-secret
  volumes:
    kanboard_data:
    kanboard_plugins:
    kanboard_ssl:

Starting the container with Docker Compose:

.. code:: bash

    docker-compose up

Build Your Own Docker Image
---------------------------

Clone the Kanboard repository and run the following command:

.. code:: bash

    make docker-image

.. note::

  You must use the SMTP method or a plugin like Mailgun/Sendgrid/Postmark to send emails.
