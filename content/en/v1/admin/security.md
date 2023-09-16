---
title: Security
toc: true
---

General Advices
---------------

- Do not forget to change the default user/password.
- Do not allow everybody to access to the directory `data` from the URL. A `.htaccess` file for Apache and a `web.config` file for IIS is included, but other web servers have to be configured manually.

{{< hint type="info" >}}
- Plugins installation from the web user interface is disabled by default.
- There is no code review or any approval process to submit a plugin.
- This is up to the Kanboard instance owner to check if a plugin is legit.
{{</ hint >}}

Installation Outside Document Root
----------------------------------

If you would like to install Kanboard outside of the web server document
root, you need to create at least these symlinks:

```bash
.
├── assets -> ../kanboard/assets
├── cli -> ../kanboard/cli
├── favicon.ico -> ../kanboard/favicon.ico
├── index.php -> ../kanboard/index.php
├── jsonrpc.php -> ../kanboard/jsonrpc.php
└── robots.txt -> ../kanboard/robots.txt
```

The `.htaccess` is optional because its content can be included directly
in the Apache configuration.

You can also define a custom location for the plugins and files folders
by changing the config file.

{{< hint type="info" >}}
Some plugins may requires to be installed into the document root.
{{</ hint >}}

Brute Force Protection
----------------------

The brute force protection of Kanboard works at the user account level:

- After 3 authentication failure for the same username, the login form
    shows a captcha image to prevent automated bot tentatives.
- After 6 authentication failure, the user account is locked for a
    period of 15 minutes.

This feature works only for authentication methods that use the login
form.

However, **after three authentication failure through the user API**,
the account has to be unlocked by using the login form.

Kanboard doesn't block any IP addresses since bots can use several
anonymous proxies. However, you can use external tools like
[fail2ban](http://www.fail2ban.org) to avoid massive scans.

Default settings can be changed with these configuration variables:

```php
// Enable captcha after 3 authentication failure
define('BRUTEFORCE_CAPTCHA', 3);

// Lock the account after 6 authentication failure
define('BRUTEFORCE_LOCKDOWN', 6);

// Lock account duration in minutes
define('BRUTEFORCE_LOCKDOWN_DURATION', 15);
```

If you don't want to wait 15 minutes, you can unlock a user from the
user interface. As administrator, go to the user profile and click on
"Unlock this user".
