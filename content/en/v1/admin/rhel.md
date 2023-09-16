---
title: Installation on RedHat/Centos/Oracle Linux Enterprise
toc: true
---

{{< hint type="warning" >}}
This page hasn\'t been updated for a while, and it\'s probably obsolete.
{{</ hint >}}

{{< hint type="danger" >}}
- Do not forget to change the default username/password.
- Do not allow everybody to access the directory `data` from the URL.
- Enable `.htaccess` if you use Apache (Option `AllowOverride All`).
- This is your responsability to configure your server correctly.
{{</ hint >}}

Centos 7
--------

Install PHP and Apache:

```bash
yum install -y php php-xml php-mbstring php-pdo php-gd unzip wget
```

By default, Centos 7 use PHP 5.4.16 and Apache 2.4.6.

Restart Apache:

```bash
systemctl restart httpd.service
```

Install Kanboard:

```bash
cd /var/www/html

# Download the latest release from https://github.com/kanboard/kanboard/releases
wget https://github.com/kanboard/kanboard/archive/v<version>.zip

unzip kanboard-<version>.zip
chown -R apache:apache kanboard-<version>/data
rm kanboard-<version>.zip
```

SELinux restrictions
--------------------

If SELinux is enabled, be sure that the Apache user can write to the
directory data:

```bash
semanage fcontext -a -t httpd_sys_rw_content_t "/var/www/html/kanboard/data(/.*)?"
restorecon -r -v /var/www/html/kanboard/data
```

Be sure to configure your server to allow Kanboard to send emails and
make external network requests, for example with SELinux:

```bash
setsebool -P httpd_can_network_connect=1
```

Allowing external connections is necessary if you use LDAP, SMTP, Web
hooks or any third-party integration.
