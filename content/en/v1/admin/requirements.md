---
title: Requirements and Prerequisites
toc: true
aliases:
    - /en/latest/admin_guide/requirements.html
    - /en/1.2.24/admin_guide/requirements.html
    - /en/1.2.23/admin_guide/requirements.html
    - /en/1.2.22/admin_guide/requirements.html
    - /en/1.2.21/admin_guide/requirements.html
    - /en/1.2.20/admin_guide/requirements.html
---

Prerequisites to install and use Kanboard.

Server Side
-----------

### Compatible Operating Systems

- Alpine Linux
- Linux Ubuntu
- Linux RHEL (RedHat, Centos, Oracle Linux, RockyLinux, etc)
- Linux Debian
- FreeBSD
- Microsoft Windows

{{< hint type="info" >}}
The recommended operating system is GNU/Linux (Debian/Ubuntu/RHEL/Alpine
Linux).
{{</ hint >}}

### Compatible Databases

- Sqlite >= 3.7
- Mysql >= 5.6
- MariaDB >= 10
- Postgresql >= 9.4
- Microsoft SQL Server (experimental - available since v1.2.25)

Which database to choose?

- Sqlite: Single user or small team (almost no concurrency)
- Mysql/Postgres: Larger team, high-availability configuration

{{< hint type="info" >}}
- The recommended database is Postgresql.
- Do not use Sqlite with NFS or with Docker.
{{</ hint >}}

### Compatible Web Servers

- Apache HTTP Server
- Nginx
- Microsoft IIS
- Caddy Server

Kanboard is pre-configured to work with Apache (URL rewriting).

{{< hint type="warning" >}}
- Kanboard is NOT compatible with Apache `mod_security`.
- If you use Apache, you must have the module `mod_version`.
{{</ hint >}}

### PHP Versions

- PHP >= 7.4
- PHP 8.x

{{< hint type="info" >}}
- Since version 1.2.22, Kanboard requires at least PHP 7.4
- Since version 1.2.13, Kanboard requires at least PHP 7.2
- The latest version of PHP is recommended.
{{</ hint >}}

### PHP Extensions Required

- `pdo_sqlite` (Only if you use Sqlite)
- `pdo_mysql` (Only if you use Mysql/MariaDB)
- `pdo_pgsql` (Only if you use Postgres)
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

### Optional PHP extensions

- `zip`: Used to install plugins from web ui
- `ldap`: Only for LDAP integration
- `curl`: Use cURL as HTTP client

### Recommendations

- Modern Linux or Unix operating system with the latest version of PHP.
- Best performances are obtained with the latest version of PHP with OpCode caching activated.

Client Side
-----------

### Browsers

Always use a modern browser with the latest version if possible:

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

- Laptop or desktop with a screen resolution >= 1366 x 768
- Tablet with a screen resolution >= 1024 x 768

Note that using Kanboard with a smartphone should work, but using the board on a small screen is not always pratical.
