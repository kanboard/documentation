---
title: Debian Installation
toc: true
menu:
    main:
        parent: Administration
---

{{< hint type="danger" >}}
- Do not forget to change the default username/password.
- Do not allow public access to the `data` directory via the URL.
- Enable `.htaccess` if you use Apache (Option `AllowOverride All`).
- It is your responsibility to configure your server correctly.
{{</ hint >}}

{{< hint type="warning" >}}
This page may contain outdated information and has not been reviewed recently. Please verify the steps and package versions before proceeding.
{{</ hint >}}

## Debian 10 (Buster)

Install Apache and PHP:

```bash
apt update
apt install -y apache2 libapache2-mod-php php-cli php-mbstring \
    php-sqlite3 php-opcache php-json php-ldap php-gd php-xml  \
    php-mysql php-pgsql php-curl php-zip

systemctl enable apache2
```

Install Kanboard:

```bash
version=1.2.13
wget https://github.com/kanboard/kanboard/archive/v$version.tar.gz
tar xzvf v$version.tar.gz -C /var/www/html/
chown -R www-data:www-data /var/www/html/kanboard-$version/data

rm v$version.tar.gz
```

{{< hint type="info" >}}
Some features of Kanboard require that you run a [daily background job]({{< relref "cronjob.md" >}}).
{{</ hint >}}
