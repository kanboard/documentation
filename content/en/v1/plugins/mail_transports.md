---
title: Mail Transport
toc: true
menu:
    main:
        parent: Developing Plugins
---

By default, Kanboard supports three standard mail transports:

- Mail (PHP mail function)
- SMTP
- Sendmail command

With the plugin API, you can add a driver for any email provider. For example, your plugin can add a mail transport for a provider that uses an HTTP API.

Implementation
--------------

Your plugin must implement the interface `Kanboard\Core\Mail\ClientInterface` and extend `Kanboard\Core\Base`.

The only method you need to implement is `sendEmail()`:

```php
interface ClientInterface
{
    /**
     * Send an HTML email
     *
     * @access public
     * @param  string $recipientEmail
     * @param  string $recipientName
     * @param  string $subject
     * @param  string $html
     * @param  string $authorName
     * @param  string $authorEmail
     */
    public function sendEmail($recipientEmail, $recipientName, $subject, $html, $authorName, $authorEmail = '');
}
```

To register your new mail transport, use the method `setTransport($transport, $class)` from the class `Kanboard\Core\Mail\Client`:

```php
$this->emailClient->setTransport('myprovider', '\Kanboard\Plugin\MyProvider\MyEmailHandler');
```

The second argument contains the fully qualified namespace of your concrete class.

Examples of mail transport plugins
----------------------------------

- [SendGrid](https://github.com/kanboard/plugin-sendgrid)
- [Mailgun](https://github.com/kanboard/plugin-mailgun)
- [Postmark](https://github.com/kanboard/plugin-postmark)
