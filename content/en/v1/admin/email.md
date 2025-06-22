---
title: Email Configuration
toc: true
menu:
    main:
        parent: Administration
---

## User Settings

To receive email notifications, Kanboard users must:

- Enable notifications in their profile.
- Provide a valid email address in their profile.
- Be a member of the project that triggers notifications.

Note: The logged-in user performing the action does not receive notifications, only other project members do.

## Email Transports

Kanboard supports several email transport methods:

- SMTP
- Sendmail
- PHP's native mail function
- Other methods provided by external plugins (e.g., Postmark, Sendgrid, Mailgun)

## Server Settings

By default, Kanboard uses PHP's built-in mail function to send emails. This typically requires no configuration if your server is already set up to send emails.

However, you can configure other methods like SMTP or Sendmail.

### SMTP Configuration

Rename the file `config.default.php` to `config.php` and update the following values:

```php
// Use "smtp" as the mail transport
define('MAIL_TRANSPORT', 'smtp');

// Define server settings
define('MAIL_SMTP_HOSTNAME', 'mail.example.com');
define('MAIL_SMTP_PORT', 25);

// Credentials for SMTP server authentication (optional)
define('MAIL_SMTP_USERNAME', 'username');
define('MAIL_SMTP_PASSWORD', 'super password');
```

The `MAIL_SMTP_ENCRYPTION` option accepts only the following values:

- `null`: No encryption.
- `ssl`: Use TLS encryption (commonly used with port 465).
- `tls`: Use STARTTLS encryption (commonly used with port 587).

Ensure you select the appropriate value based on your SMTP server's requirements.

Example to use the port 465 and TLS:

```php
define('MAIL_SMTP_PORT', 465);
define('MAIL_SMTP_ENCRYPTION', 'ssl');
```

Example to use the port 587 and `STARTTLS`:

```php
define('MAIL_SMTP_PORT', 587);
define('MAIL_SMTP_ENCRYPTION', 'tls');
```

Some servers reject emails based on the hostname transmitted with the HELO (EHLO) command (see RFC 5321). You can explicitly set the hostname used in the HELO command:

```php
define('MAIL_SMTP_HELO_NAME', null); // Valid: null (default) or FQDN
```

### Sendmail Configuration

By default, the Sendmail command is `/usr/sbin/sendmail -bs`. You can customize it in your config file.

Example:

```php
// Use "sendmail" as the mail transport
define('MAIL_TRANSPORT', 'sendmail');

// Customize the Sendmail command if needed
define('MAIL_SENDMAIL_COMMAND', '/usr/sbin/sendmail -bs');
```

### PHP Built-in Mail Function

This is the default configuration:

```php
define('MAIL_TRANSPORT', 'mail');
```

The PHP built-in mail feature relies on the configuration in the `php.ini` file. For more details, refer to the official PHP documentation: [PHP Mail Configuration](https://www.php.net/manual/en/mail.configuration.php).

### Sender Email Address

By default, emails use the sender address `notifications@kanboard.local`. This address is not configured to receive replies.

You can customize the sender address by changing the `MAIL_FROM` constant in your config file:

```php
define('MAIL_FROM', 'kanboard@mydomain.tld');
```

This is useful if your SMTP server does not accept the default address.

### Kanboard URL

You must define explicitly the application URL to generate correct links in the emails otherwise the links will default to `http://localhost/` domain.

## Troubleshooting

If no emails are sent and you are confident that everything is configured correctly:

- Check your spam folder.
- Enable debug mode and check the debug file `data/debug.log` for errors.
- Ensure your server or hosting provider allows outgoing emails.
- If you use SELinux, allow PHP to send emails.
