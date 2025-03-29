---
title: Requirements and Prerequisites
toc: true
menu:
    main:
        parent: Administration
aliases:
    - /en/latest/admin_guide/requirements.html
    - /en/1.2.24/admin_guide/requirements.html
    - /en/1.2.23/admin_guide/requirements.html
    - /en/1.2.22/admin_guide/requirements.html
    - /en/1.2.21/admin_guide/requirements.html
    - /en/1.2.20/admin_guide/requirements.html
---

Prerequisites to install and use Kanboard.

## Server Side

### Compatible Operating Systems

- Alpine Linux
- Linux Ubuntu
- Linux RHEL (RedHat, CentOS, Oracle Linux, RockyLinux, etc.)
- Linux Debian
- FreeBSD
- Microsoft Windows

{{< hint type="info" >}}
The recommended operating system is GNU/Linux (Debian/Ubuntu/RHEL/Alpine Linux).
{{</ hint >}}

### Compatible Databases

- SQLite >= 3.7
- MySQL >= 5.6
- MariaDB >= 10
- PostgreSQL >= 9.4
- Microsoft SQL Server (experimental - available since v1.2.25)

**Which database to choose?**

- SQLite: For a single user or small teams (minimal concurrency).
- MySQL/PostgreSQL: For larger teams or high-availability configurations.

{{< hint type="info" >}}
- The recommended database is PostgreSQL.
- Do not use SQLite with NFS or Docker.
{{</ hint >}}

### Compatible Web Servers

- Apache HTTP Server
- Nginx
- Microsoft IIS
- Caddy Server

Kanboard is pre-configured to work with Apache (URL rewriting).

{{< hint type="warning" >}}
- Kanboard is NOT compatible with Apache `mod_security`.
- If you use Apache, you must have the `mod_version` module enabled.
{{</ hint >}}

### PHP Versions

- PHP >= 7.4
- PHP 8.x

{{< hint type="info" >}}
- Since version 1.2.22, Kanboard requires at least PHP 7.4.
- Since version 1.2.13, Kanboard requires at least PHP 7.2.
- The latest version of PHP is recommended.
{{</ hint >}}

### Required PHP Extensions

- `pdo_sqlite` (Only if you use SQLite)
- `pdo_mysql` (Only if you use MySQL/MariaDB)
- `pdo_pgsql` (Only if you use PostgreSQL)
- `gd`
- `mbstring`
- `openssl`
- `json`
- `hash`
- `ctype`
- `session`
- `filter`
- `xml`
- `SimpleXML`
- `dom`

### Optional PHP Extensions

- `zip`: Used to install plugins from the web UI.
- `ldap`: Only for LDAP integration.
- `curl`: Used as an HTTP client.

### Recommendations

- A modern Linux or Unix operating system with the latest version of PHP.
- Best performance is achieved with the latest version of PHP and OpCode caching enabled.

## Client Side

### Browsers

Always use a modern browser with the latest version:

- Safari
- Google Chrome
- Mozilla Firefox
- Microsoft Edge

{{< hint type="info" >}}
The recommended browsers are Mozilla Firefox or Google Chrome.
{{</ hint >}}

{{< hint type="warning" >}}
Microsoft Internet Explorer is not supported since Kanboard version 1.2.11.
{{</ hint >}}

### Devices

- Laptop or desktop with a screen resolution >= 1366 x 768.
- Tablet with a screen resolution >= 1024 x 768.

Note: Using Kanboard on a smartphone should work, but the board may not be practical to use on small screens.
