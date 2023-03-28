---
title: Docker Image Usage
toc: true
aliases:
  - /en/latest/admin_guide/docker.html
  - /en/1.2.24/admin_guide/docker.html
  - /en/1.2.23/admin_guide/docker.html
  - /en/1.2.22/admin_guide/docker.html
  - /en/1.2.21/admin_guide/docker.html
  - /en/1.2.20/admin_guide/docker.html
---

{{< hint type="warning" >}}
Please, do not update the software blindly without reading the
[ChangeLog](https://github.com/kanboard/kanboard/blob/master/ChangeLog).
Always check for breaking changes if any.
{{</ hint >}}

Docker Registries
-----------------

Registry Name               | Registry URL
----------------------------| -----------------------------------------
[Docker Hub](https://hub.docker.com/r/kanboard/kanboard) | `docker.io/kanboard/kanboard`
[GitHub Container Registry](https://github.com/orgs/kanboard/packages/container/package/kanboard) | `ghcr.io/kanboard/kanboard`

Docker Tags
-----------

Tag           | Description
--------------| -------------------------------------------------------
`latest`      | Latest stable release
`nightly`     | Nightly build (latest development changes)
`v1.2.x`      | Specific version of Kanboard

The recommendation is to always pin a specific version of Kanboard to avoid unexpected upgrade.

Environment Variables
---------------------

All Kanboard [configuration options]({{< relref "config.md" >}}) can be used as environment variable.

Volumes
-------

Path                    | Description
------------------------|------------------------------------------------
`/var/www/app/data`     | Application data (Sqlite database, attachments, etc.)
`/var/www/app/plugins`  | Plugins
`/etc/nginx/ssl`        | SSL certificates

Custom Config File
------------------

- The container already includes a custom config file located at `/var/www/app/config.php`.
- You can store your own config file on the data volume: `/var/www/app/data/config.php`.
- You must restart the container to take into account the new parameters of your custom config file.

Running the Container
---------------------

### Basic Usage

```bash
docker run -d --name kanboard -p 80:80 -t kanboard/kanboard:v1.2.8
```

### Docker Compose

There is a `docker-compose.yml` file in Kanboard repository. Here an
example with Sqlite:

```yaml
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
```

Another example with MariaDB:

```yaml
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
    - db:/var/lib/mysql
volumes:
  kanboard_data:
  kanboard_plugins:
  kanboard_ssl:
  db:
```

Starting the container with Docker Compose:

```bash
docker compose up
```

By default, [the installation of plugins is disabled for security reasons]({{< relref "plugins.md" >}}). 
Here is an example to enable the installation of plugins:

```bash
docker run --rm \
  --name=kanboard \
  -p 8080:80 \
  -e PLUGIN_INSTALLER=true \
  kanboard/kanboard:latest
```

Another example with Docker Compose and volumes:

```yaml
version: '2'
services:
  kanboard:
    image: kanboard/kanboard:latest
    ports:
     - "8080:80"
     - "443:443"
    volumes:
     - kanboard_data:/var/www/app/data
     - kanboard_plugins:/var/www/app/plugins
     - kanboard_ssl:/etc/nginx/ssl
    environment:
      - PLUGIN_INSTALLER=true
volumes:
  kanboard_data:
    driver: local
  kanboard_plugins:
    driver: local
  kanboard_ssl:
    driver: local
```

Build Your Own Docker Image
---------------------------

Clone the Kanboard repository and run the following command:

```bash
make docker-image
```

{{< hint type="info" >}}
You must use the SMTP method, or a plugin like Mailgun/Sendgrid/Postmark to send emails.
{{</ hint >}}
