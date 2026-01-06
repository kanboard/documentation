---
title: Security
toc: true
menu:
    main:
        parent: Administration
---

General Advice
--------------

- Change the default username and password immediately after installation.
- **Do not expose Kanboard directly to untrusted networks** (e.g., the public Internet); restrict access with a firewall or VPN and/or place it behind a properly configured reverse proxy.
- Prevent public access to the `data` directory via the URL. A `.htaccess` file for Apache and a `web.config` file for IIS are included; configure other web servers accordingly.
- When using a reverse proxy, ensure it strips or overwrites incoming `X-Forwarded-*` headers to avoid HTTP header spoofing, and **only forwards trusted values to Kanboard**.
- **Add rate limiting / throttling** (for example at the reverse proxy or web server) to reduce brute-force attempts.
- Be cautious with webhooks, integrations, and plugin features that fetch remote URLs: **untrusted URL configuration can lead to SSRF** (Server-Side Request Forgery). **Restrict who can configure those URLs and limit outbound network access from the Kanboard server** (e.g., block access to internal networks and metadata services).

{{< hint type="info" >}}
- Plugin installation from the web user interface is disabled by default.
- There is no code review or approval process for submitting plugins.
- It is the responsibility of the Kanboard instance owner to verify the legitimacy of a plugin.
{{</ hint >}}

Installation Outside Document Root
----------------------------------

If you want to install Kanboard outside the web server's document root, you need to create at least these symlinks:

```bash
.
├── assets -> ../kanboard/assets
├── cli -> ../kanboard/cli
├── favicon.ico -> ../kanboard/favicon.ico
├── index.php -> ../kanboard/index.php
├── jsonrpc.php -> ../kanboard/jsonrpc.php
└── robots.txt -> ../kanboard/robots.txt
```

The `.htaccess` file is optional because its content can be included directly in the Apache configuration.

You can also define a custom location for the plugins and files folders by modifying the configuration file.

{{< hint type="info" >}}
Some plugins may require installation in the document root.
{{</ hint >}}

Brute Force Protection
----------------------

Kanboard's brute force protection works at the user account level:

- After 3 failed login attempts for the same username, the login form displays a CAPTCHA to prevent automated bot attempts.
- After 6 failed login attempts, the user account is locked for 15 minutes.

This feature works only for authentication methods that use the login form.

However, **after three failed authentication attempts via the user API**, the account must be unlocked using the login form.

Kanboard does not block IP addresses since bots can use multiple anonymous proxies. However, you can use external tools like [fail2ban](http://www.fail2ban.org) to prevent massive scans.

Default settings can be changed using these configuration variables:

```php
// Enable CAPTCHA after 3 failed login attempts
define('BRUTEFORCE_CAPTCHA', 3);

// Lock the account after 6 failed login attempts
define('BRUTEFORCE_LOCKDOWN', 6);

// Lock account duration in minutes
define('BRUTEFORCE_LOCKDOWN_DURATION', 15);
```

If you do not want to wait 15 minutes, you can unlock a user from the user interface. As an administrator, go to the user profile and click on "Unlock this user."
