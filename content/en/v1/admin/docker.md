---
title: Docker Image Usage
toc: true
menu:
    main:
        parent: Administration
aliases:
  - /en/latest/admin_guide/docker.html
  - /en/1.2.24/admin_guide/docker.html
  - /en/1.2.23/admin_guide/docker.html
  - /en/1.2.22/admin_guide/docker.html
  - /en/1.2.21/admin_guide/docker.html
  - /en/1.2.20/admin_guide/docker.html
---

{{< hint type="warning" >}}
Do not update the software blindly without reading the [ChangeLog](https://github.com/kanboard/kanboard/blob/master/ChangeLog). Always check for breaking changes.
{{</ hint >}}

## Docker Registries

| Registry Name               | Registry URL                                                                 |
|-----------------------------|-----------------------------------------------------------------------------|
| [Docker Hub](https://hub.docker.com/r/kanboard/kanboard) | `docker.io/kanboard/kanboard`                                                  |
| [GitHub Container Registry](https://github.com/orgs/kanboard/packages/container/package/kanboard) | `ghcr.io/kanboard/kanboard` |
| [Quay.io](https://quay.io/repository/kanboard/kanboard) | `quay.io/kanboard/kanboard`                                                   |

## Docker Tags

| Tag       | Description                                   |
|-----------|-----------------------------------------------|
| `latest`  | Latest stable release                        |
| `nightly` | Nightly build (latest development changes)   |
| `v1.2.x`  | Specific version of Kanboard                 |

It is recommended to always pin a specific version of Kanboard to avoid unexpected upgrades.

## Volumes

| Path                    | Description                                      |
|-------------------------|--------------------------------------------------|
| `/var/www/app/data`     | Application data (SQLite database, attachments, etc.) |
| `/var/www/app/plugins`  | Plugins                                          |
| `/etc/nginx/ssl`        | SSL certificates                                |

## Environment Variables

All Kanboard [configuration options]({{< relref "config.md" >}}) can be set as environment variables.

## Custom Config File

- The container includes a default config file located at `/var/www/app/config.php`.
- You can store your custom config file in the data volume: `/var/www/app/data/config.php`.
- Restart the container to apply changes to your custom config file.

## Health Check

Since Kanboard 1.2.46, a health check endpoint is available that can be used for Kubernetes liveness and readiness probes.

```bash
curl http://localhost/healthcheck.php
{"status":200, "message":"Database connection is OK"}
```
This endpoint returns a JSON response with a `200 OK` HTTP status code when all checks pass, or a `503 Service Unavailable` status if a problem is detected.
Currently, this script only checks database connectivity.

## Running the Container

### Basic Usage

```bash
docker run -d --name kanboard -p 80:80 -t kanboard/kanboard:v1.2.45
```

### Enabling Plugins

To enable plugin installation from the web ui (disabled by default for security reasons), the `PLUGIN_INSTALLER` option must be set to `true`. Use the following example:

```bash
docker run --rm \
  --name=kanboard \
  -p 8080:80 \
  -e PLUGIN_INSTALLER=true \
  kanboard/kanboard:latest
```

### Docker Compose

You can use Docker Compose to run Kanboard. The following examples show how to set up Kanboard with SQLite, MariaDB, and PostgreSQL.
You are strongly encouraged to customize the configuration to suit your needs.

Sqlite example: https://github.com/kanboard/kanboard/blob/main/docker-compose.sqlite.yml

```yaml
name: kanboard
services:
  app:
    image: ${KANBOARD_IMAGE:-kanboard/kanboard:latest}
    container_name: kanboard
    restart: always
    ports:
     - "80:80"
     - "443:443"
    volumes:
     - data:/var/www/app/data
     - plugins:/var/www/app/plugins
     - certs:/etc/nginx/ssl
    environment:
     - PLUGIN_INSTALLER=false # Swap to true to enable web based plugin installation
volumes:
  data:
    driver: local
  plugins:
    driver: local
  certs:
    driver: local
```

MariaDB example: https://github.com/kanboard/kanboard/blob/main/docker-compose.mysql.yml

```yaml
name: kanboard
services:
  app:
    image: ${KANBOARD_IMAGE:-kanboard/kanboard:latest}
    container_name: kanboard
    restart: always
    ports:
     - "80:80"
     - "443:443"
    volumes:
     - data:/var/www/app/data
     - plugins:/var/www/app/plugins
     - certs:/etc/nginx/ssl
    environment:
      DATABASE_URL: mysql://kanboard:kanboard-secret@db/kanboard
    depends_on:
      db:
        condition: service_healthy
  db:
    image: mariadb:lts
    command: --default-authentication-plugin=mysql_native_password
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: kanboard
      MYSQL_USER: kanboard
      MYSQL_PASSWORD: kanboard-secret
    volumes:
      - db:/var/lib/mysql
    healthcheck:
      test: ["CMD", "healthcheck.sh", "--connect", "--innodb_initialized"]
      interval: 10s
      timeout: 5s
      retries: 5
volumes:
  data:
    driver: local
  plugins:
    driver: local
  certs:
    driver: local
  db:
    driver: local
```

Postgres example: https://github.com/kanboard/kanboard/blob/main/docker-compose.postgres.yml

```yaml
name: kanboard
services:
  app:
    image: ${KANBOARD_IMAGE:-kanboard/kanboard:latest}
    container_name: kanboard
    restart: always
    ports:
     - "80:80"
     - "443:443"
    volumes:
     - data:/var/www/app/data
     - plugins:/var/www/app/plugins
     - certs:/etc/nginx/ssl
    environment:
      DATABASE_URL: postgres://kanboard:kanboard-secret@db/kanboard
    depends_on:
      db:
        condition: service_healthy
  db:
    image: postgres:latest
    restart: always
    environment:
      POSTGRES_USER: kanboard
      POSTGRES_PASSWORD: kanboard-secret
      POSTGRES_DB: kanboard
    volumes:
      - db:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD", "pg_isready", "-U", "kanboard"]
      start_period: 15s
      interval: 10s
      timeout: 5s
volumes:
  data:
    driver: local
  plugins:
    driver: local
  certs:
    driver: local
  db:
    driver: local
```

Start the container with Docker Compose:

```bash
docker compose up
```

## Build Your Own Docker Image

Clone the Kanboard repository and run the following command:

```bash
make docker-image
```

## Notes

- You must use the SMTP method or a plugin like Mailgun/Sendgrid/Postmark to send emails.
- The `mail` and `sendmail` transports will not work with the official Docker image.
