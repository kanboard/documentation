---
title: Installation on RedHat/CentOS/Oracle Linux Enterprise
toc: true
menu:
    main:
        parent: Administration
---

{{< hint type="warning" >}}
This page hasn't been updated for a while and may be obsolete.
{{</ hint >}}

{{< hint type="danger" >}}
- Change the default username/password.
- Prevent public access to the `data` directory via the URL.
- Enable `.htaccess` if you use Apache (Option `AllowOverride All`).
- It is your responsibility to configure your server correctly.
{{</ hint >}}

## CentOS 7

Install PHP and Apache:

```bash
yum install -y php php-xml php-mbstring php-pdo php-gd unzip wget
```

By default, CentOS 7 uses PHP 5.4.16 and Apache 2.4.6.

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

## SELinux Restrictions

If SELinux is enabled, ensure that the Apache user can write to the `data` directory:

```bash
semanage fcontext -a -t httpd_sys_rw_content_t "/var/www/html/kanboard/data(/.*)?"
restorecon -r -v /var/www/html/kanboard/data
```

Ensure your server is configured to allow Kanboard to send emails and make external network requests. For example, with SELinux:

```bash
setsebool -P httpd_can_network_connect=1
```

Allowing external connections is necessary if you use LDAP, SMTP, webhooks, or any third-party integration.
