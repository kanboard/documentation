---
title: Configuration File
toc: true
menu:
    main:
        parent: Administration
---

You can customize the default settings of Kanboard by adding a file `config.php` at the project root or in the `data` folder. You can also rename the file `config.default.php` to `config.php` and change the desired values.

All Kanboard configuration options are also available as environment variables.

## Enable/Disable Debug Mode

```php
define('DEBUG', true);
define('LOG_DRIVER', 'file'); // Other drivers are: syslog, stdout, stderr, system, or file

// By default, the log file is in data/debug.log but you can change the path:
define('LOG_FILE', '/path/to/debug.log');
```

- The log driver must be defined if you enable the debug mode.
- The debug mode logs all SQL queries and the time taken to generate pages.
- The `system` driver uses the built-in PHP logger, which can be configured in the [php.ini](http://php.net/manual/en/errorfunc.configuration.php#ini.error-log). By default, log messages are sent to the web server logs.

## Plugins

Plugin folder:

```php
define('PLUGINS_DIR', 'data/plugins');
```

Enable/disable plugin installation from the user interface:

```php
define('PLUGIN_INSTALLER', false); // Default is false since Kanboard v1.2.8
```

Change the default plugin directory URL:

```php
define('PLUGIN_API_URL', 'https://kanboard.org/plugins.json');
```

## Folder for Uploaded Files

```php
define('FILES_DIR', 'data/files');
```

## Cache Parameters

```php
// Available cache drivers are "file" and "memory"
define('CACHE_DRIVER', 'memory');

// Cache folder to use if cache driver is "file" (must be writable by the web server user)
define('CACHE_DIR', DATA_DIR.DIRECTORY_SEPARATOR.'cache');
```

## Enable/Disable URL Rewrite

```php
define('ENABLE_URL_REWRITE', false);
```

## Email Configuration

```php
// Enable/disable email configuration from the user interface
define('MAIL_CONFIGURATION', true);

// E-mail address used for the "From" header (notifications)
define('MAIL_FROM', 'notifications@kanboard.local');

// Mail transport to use: "smtp", "sendmail" or "mail" (PHP mail function)
define('MAIL_TRANSPORT', 'mail');

// SMTP configuration to use when the "smtp" transport is chosen
define('MAIL_SMTP_HOSTNAME', '');
define('MAIL_SMTP_PORT', 25);
define('MAIL_SMTP_USERNAME', '');
define('MAIL_SMTP_PASSWORD', '');
define('MAIL_SMTP_HELO_NAME', null); // valid: null (default), or FQDN
define('MAIL_SMTP_ENCRYPTION', null); // Valid values are "null", "ssl", or "tls"

// Sendmail command to use when the transport is "sendmail"
define('MAIL_SENDMAIL_COMMAND', '/usr/sbin/sendmail -bs');

// E-mail address used for the "Bcc" header to send a copy of all notifications
define('MAIL_BCC', '');
```

## Database Settings

```php
// Run database migrations automatically
// If set to false, you will have to run the SQL migrations manually during the next Kanboard upgrade
define('DB_RUN_MIGRATIONS', true);

// Database driver: sqlite, mysql, or postgres (sqlite by default)
define('DB_DRIVER', 'sqlite');

// Enable or disable SQLite WAL mode
define('DB_WAL_MODE', true);

// MySQL/Postgres username
define('DB_USERNAME', 'root');

// MySQL/Postgres password
define('DB_PASSWORD', '');

// MySQL/Postgres hostname
define('DB_HOSTNAME', 'localhost');

// MySQL/Postgres database name
define('DB_NAME', 'kanboard');

// MySQL/Postgres custom port (null = default port)
define('DB_PORT', null);

// MySQL SSL key
define('DB_SSL_KEY', null);

// MySQL SSL certificate
define('DB_SSL_CERT', null);

// MySQL SSL CA
define('DB_SSL_CA', null);
```

## LDAP Settings

```php
// Enable LDAP authentication (false by default)
define('LDAP_AUTH', false);

// LDAP server hostname
define('LDAP_SERVER', '');

// LDAP server port (389 by default)
define('LDAP_PORT', 389);

// Require certificate verification for ldaps:// URLs. Set to false to skip verification
define('LDAP_SSL_VERIFY', true);

// Enable LDAP START_TLS
define('LDAP_START_TLS', false);

// By default, Kanboard lowercases the LDAP username to avoid duplicate users (the database is case-sensitive)
// Set to true if you want to preserve the case
define('LDAP_USERNAME_CASE_SENSITIVE', false);

// LDAP bind type: "anonymous", "user", or "proxy"
define('LDAP_BIND_TYPE', 'anonymous');

// LDAP username to use with proxy mode
// LDAP username pattern to use with user mode
define('LDAP_USERNAME', null);

// LDAP password to use for proxy mode
define('LDAP_PASSWORD', null);

// LDAP DN for users
define('LDAP_USER_BASE_DN', '');

// LDAP pattern to use when searching for a user account
define('LDAP_USER_FILTER', '');

// LDAP attribute for username
define('LDAP_USER_ATTRIBUTE_USERNAME', 'uid');

// LDAP attribute for user full name
define('LDAP_USER_ATTRIBUTE_FULLNAME', 'cn');

// LDAP attribute for user email
define('LDAP_USER_ATTRIBUTE_EMAIL', 'mail');

// LDAP attribute for user avatar image: thumbnailPhoto or jpegPhoto
define('LDAP_USER_ATTRIBUTE_PHOTO', '');

// Allow automatic LDAP user creation
define('LDAP_USER_CREATION', true);
```

## Reverse-Proxy Authentication Settings

```php
// Enable/disable reverse proxy authentication
define('REVERSE_PROXY_AUTH', false);

// Header name to use for the username
define('REVERSE_PROXY_USER_HEADER', 'REMOTE_USER');

// Header name to use for the user email
define('REVERSE_PROXY_EMAIL_HEADER', 'REMOTE_EMAIL');

// Header name to use for the user full name
define('REVERSE_PROXY_FULLNAME_HEADER', 'REMOTE_NAME');

// Username of the admin, by default blank
define('REVERSE_PROXY_DEFAULT_ADMIN', '');

// Default domain to use for setting the email address
define('REVERSE_PROXY_DEFAULT_DOMAIN', '');
```

## Miscellaneous Settings

```php
// Escape HTML inside markdown text
define('MARKDOWN_ESCAPE_HTML', true);

// API alternative authentication header
define('API_AUTHENTICATION_HEADER', '');

// Hide login form, useful if all your users use external authentication
define('HIDE_LOGIN_FORM', false);

// Disable logout (for external SSO authentication)
define('DISABLE_LOGOUT', false);

// Override API token stored in the database, useful for automated tests
define('API_AUTHENTICATION_TOKEN', 'My unique API Token');

// TOTP (2FA) issuer name
define('TOTP_ISSUER', 'Kanboard');

// Comma separated list of trusted proxy headers, for example: "HTTP_X_REAL_IP,HTTP_X_FORWARDED_FOR"
define('TRUSTED_PROXY_HEADERS', '');

// Comma separated list of trusted proxy IP networks (CIDR), for example: "192.168.0.0/16,10.0.0.0/8,::1/128"
define('TRUSTED_PROXY_NETWORKS', '');

// Allow private network access when fetching metadata for external links
define('EXTERNAL_LINK_ALLOW_PRIVATE_NETWORKS', false);
```
