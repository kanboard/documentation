---
title: Installation on Microsoft Windows Server
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

## Windows Server and Apache

This guide provides step-by-step instructions to set up Kanboard on a Windows Server with Apache and PHP.

Note: If you have a 64-bit platform, choose "x64"; otherwise, choose "x86" for 32-bit systems.

### Visual C++ Redistributable Installation

PHP and Apache are compiled with Visual Studio, so you need to install this library if it's not already installed.

1. Download the library from the [official Microsoft website](http://www.microsoft.com/en-us/download/details.aspx?id=30679).
2. Run the installer `vcredist_x64.exe` or `vcredist_x86.exe` according to your platform.

#### Apache Installation

1. Download the Apache binary from [Apache Lounge](http://www.apachelounge.com/download/).
2. Unzip the `Apache24` folder to `C:\Apache24`.

Define the server name:

Open the file `C:\Apache24\conf\httpd.conf` and add the directive:

    ServerName localhost

### Install the Apache Service

Open a command prompt (`cmd.exe`) and navigate to the directory `C:\Apache24\bin`:

```bash
cd C:\Apache24\bin

# Install the Windows service
httpd.exe -k install
```

### Install ApacheMonitor

- Double-click on `C:\Apache24\bin\ApacheMonitor.exe`, or add it to your startup folder.
- Right-click on the icon and start Apache.

### Check the Apache Installation

Visit <http://localhost/>. You should see a blank page with the text "It works!".

### PHP Installation

1. Download the latest stable version of PHP from the [official PHP website](http://windows.php.net/download/). Choose the **Thread Safe** version and ensure it matches the Apache build type (x86 or x64).
2. Unzip the files to `C:\php`.
3. Navigate to the PHP folder and rename the file `php.ini-production` to `php.ini`.

Edit the `php.ini` file:

Uncomment the extension directory:

```ini
extension_dir = "C:/php/ext"
```

Uncomment these PHP modules:

```ini
extension=php_gd2.dll
extension=php_ldap.dll
extension=php_mbstring.dll
extension=php_openssl.dll
extension=php_pdo_sqlite.dll
```

Set the time zone:

```ini
date.timezone = America/Montreal
```

Refer to the [PHP documentation](http://php.net/manual/en/timezones.america.php) for a list of supported time zones.

Load the PHP module for Apache:

Add the following configuration to `C:\Apache24\conf\httpd.conf`:

    LoadModule php5_module "c:/php/php5apache2_4.dll"
    AddHandler application/x-httpd-php .php

    # Configure the path to php.ini
    PHPIniDir "C:/php"

    # Update this directive
    DirectoryIndex index.php index.html

Restart Apache.

Test your PHP installation:

Create a file named `phpinfo.php` in the folder `C:\Apache24\htdocs`:

```php
<?php

phpinfo();
?>
```

Visit <http://localhost/phpinfo.php>. You should see detailed information about your PHP installation.

### Kanboard Installation

1. Download the zip file.
2. Extract the archive to `C:\Apache24\htdocs\kanboard`.
3. Open your web browser and navigate to <http://localhost/kanboard/>.
4. The default credentials are **admin/admin**.

## Windows Server and IIS

This guide provides step-by-step instructions to set up Kanboard on a Windows Server with IIS and PHP.

### PHP Installation

1. Install IIS on your server (add a new role and enable CGI/FastCGI).
2. Follow the official PHP installation documentation:
    - [Microsoft IIS 5.1 and IIS 6.0](http://php.net/manual/en/install.windows.iis6.php)
    - [Microsoft IIS 7.0 and later](http://php.net/manual/en/install.windows.iis7.php)
    - [PHP for Windows](http://windows.php.net/download/)

### PHP.ini Configuration

Ensure the following extensions are enabled in your `php.ini` file:

```ini
extension=php_gd2.dll
extension=php_ldap.dll
extension=php_mbstring.dll
extension=php_openssl.dll
extension=php_pdo_sqlite.dll
```

Set the time zone:

```ini
date.timezone = America/Montreal
```

Refer to the [PHP documentation](http://php.net/manual/en/timezones.america.php) for a list of supported time zones.

{{< hint type="info" >}}
- Ensure the required PHP extensions are enabled.
- If you encounter an error about "the library MSVCP110.dll is missing," download the Visual C++ Redistributable for Visual Studio from the Microsoft website.
{{</ hint >}}

### IIS Modules

The Kanboard archive includes a `web.config` file to enable URL rewriting. This configuration requires the [Rewrite module for IIS](http://www.iis.net/learn/extensions/url-rewrite-module/using-the-url-rewrite-module).

If the rewrite module is not installed, you will encounter a 500 Internal Server Error. If you prefer not to use URL rewriting, you can remove the `web.config` file.

### Kanboard Installation

1. Download the zip file.
2. Extract the archive to `C:\inetpub\wwwroot\kanboard`.
3. Ensure the `data` directory is writable by the IIS user.
4. Open your web browser and navigate to <http://localhost/kanboard/>.
5. The default credentials are **admin/admin**.
