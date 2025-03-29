---
title: Reverse Proxy Authentication
toc: true
menu:
    main:
        parent: Administration
---

This authentication method is often used for [SSO](http://en.wikipedia.org/wiki/Single_sign-on) (Single Sign-On), especially for large organizations.

The authentication is handled by another system. Kanboard does not store your password and assumes you are already authenticated.

## Requirements

- Apache authentication on the same server or a properly configured reverse proxy.

## How Does This Work?

1. Your reverse proxy authenticates the user and sends the username through an HTTP header.
2. Kanboard retrieves the username from the request:
    - The user is created automatically if necessary.
    - A new Kanboard session is opened without any prompt, assuming the authentication is valid.

## Installation Instructions

### Setting Up Your Reverse Proxy

This is outside the scope of this documentation. Ensure the reverse proxy sends the user login via an HTTP header and identify which header is used.

### Setting Up Kanboard

Create a custom `config.php` file or copy the `config.default.php` file:

```php
<?php

// Enable/disable reverse proxy authentication
define('REVERSE_PROXY_AUTH', true); // Set this value to true

// The HTTP header to retrieve. If not specified, REMOTE_USER is the default
define('REVERSE_PROXY_USER_HEADER', 'REMOTE_USER');

// The default Kanboard admin for your organization.
// Since everything should be filtered by the reverse proxy,
// you may want to have a bootstrap admin user.
define('REVERSE_PROXY_DEFAULT_ADMIN', 'myadmin');

// The default domain to assume for the email address.
// If the username is not an email address, it
// will be updated automatically as USER@mydomain.com
define('REVERSE_PROXY_DEFAULT_DOMAIN', 'mydomain.com');

// Header name to use for the user email (optional)
define('REVERSE_PROXY_EMAIL_HEADER', 'REMOTE_EMAIL');

// Header name to use for the user full name (optional)
define('REVERSE_PROXY_FULLNAME_HEADER', 'REMOTE_NAME');
```

{{< hint type="info" >}}
- If the proxy is the same web server that runs Kanboard, according to the [CGI protocol](http://www.ietf.org/rfc/rfc3875), the header name will be `REMOTE_USER`. For example, Apache adds `REMOTE_USER` by default if `Require valid-user` is set.
- If you use a different header for `REVERSE_PROXY_USER_HEADER`, the value must be prefixed by `HTTP_`, all hyphens must be replaced by underscores, and the string must be in all capitals because it is fetched from the `$_SERVER` array. For example, `X-Proxy-Username` becomes `HTTP_X_PROXY_USERNAME`.
- If Apache is a reverse proxy to another Apache running Kanboard, the header `REMOTE_USER` is not set (the same behavior applies to IIS and Nginx).
- If you have a real reverse proxy, the [HTTP ICAP draft](http://tools.ietf.org/html/draft-stecher-icap-subid-00#section-3.4) proposes the header to be `X-Authenticated-User`. This de facto standard has been adopted by several tools.
{{</ hint >}}
