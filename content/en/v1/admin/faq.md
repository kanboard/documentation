---
title: Frequently Asked Questions
toc: true
menu:
    main:
        parent: Administration
---

## Can you recommend a web hosting provider for Kanboard?

Kanboard works well with any reliable VPS hosting provider such as [Digital Ocean](https://www.digitalocean.com/), [Linode](https://www.linode.com/), [Gandi](https://www.gandi.net/), or others.

For optimal performance, choose a provider with fast disk I/O because Kanboard uses SQLite by default. Avoid hosting providers that use a shared NFS mount point.

{{< hint type="info" >}}
Using a shared hosting provider is not recommended. Use your own server instead.
{{</ hint >}}

## How to display a link to the task in notifications?

To enable this, specify the URL of your Kanboard installation in the Application Settings. By default, no URL is defined, so no links will be displayed.

Examples:

- <http://myserver/kanboard/>
- <http://kanboard.mydomain.com/>

Don't forget the trailing slash `/`.

This must be defined manually because Kanboard cannot infer the URL from a command-line script, and some configurations are highly specific.

## Why does the URL seem wrong (&amp;) and result in "Page not found"?

- The URL appears as `/?controller=auth&amp;action=login&amp;redirect_query=` instead of `?controller=auth&action=login&redirect_query=`.
- Kanboard returns a "Page not found" error.

This issue arises from your PHP configuration. The value of `arg_separator.output` is not set to PHP's default. Here are ways to fix it:

1. Change the value directly in your `php.ini`:

   ```ini
   arg_separator.output = "&"
   ```

2. Override the value with a `.htaccess` file:

   ```apache
   php_value arg_separator.output "&"
   ```

If neither is possible, Kanboard will attempt to override the value directly in PHP.

## Authentication failure with the API and Apache + PHP-FPM

By default, `php-cgi` under Apache does not pass HTTP Basic user/pass to PHP. To fix this, add the following lines to your `.htaccess` file:

```apache
RewriteCond %{HTTP:Authorization} ^(.+)$
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
```

## How to test Kanboard with PHP's built-in web server?

If you don't want to install a web server like Apache on localhost, you can test Kanboard using PHP's [built-in web server](http://www.php.net/manual/en/features.commandline.webserver.php):

```bash
unzip kanboard-VERSION.zip
cd kanboard
php -S localhost:8000
open http://localhost:8000/
```

## I get a blank page after installing or upgrading Kanboard

- Ensure all requirements are installed on your server.
- Check the PHP and Apache error logs.
- Verify that the files have the correct permissions.
- If you use aggressive OPcode caching, reload your web server or PHP-FPM.

## How to solve database migration issues?

- SQL migrations are executed automatically when you upgrade Kanboard to a new version.
- For PostgreSQL and MySQL, the current schema version number is stored in the `schema_version` table. For SQLite, it is stored in the `user_version` variable.
- Migrations are defined in the file `app/Schema/<DatabaseType>.php`.
- Each function represents a migration and is executed in a transaction. If a migration fails, a rollback is performed.

### Steps to fix migration issues manually:

1. Open the file corresponding to your database (`app/Schema/Sqlite.php` or `app/Schema/Mysql.php`).
2. Locate the failed migration function.
3. Execute the SQL queries defined in the function manually.
4. If you encounter an error, report it to the bug tracker with the exact SQL error.
5. Once all SQL statements are executed, update the schema version number.
6. Run the remaining migrations.

## How to change the attachment size limit?

The file upload size is determined by PHP and your web server, not Kanboard.

In your `php.ini`, update the following lines:

```ini
# Set size limit to 20MB
upload_max_filesize = 20M
post_max_size = 20M
```

If you use Nginx, define this value:

```nginx
client_max_body_size 20M;
```

Refer to the [Nginx documentation](http://nginx.org/en/docs/http/ngx_http_core_module.html#client_max_body_size) for more details.

## Why is there no official native mobile application?

The development of a native mobile application is left to the community due to the following reasons:

- Developing a native app for each platform (iOS/Android) and device type (smartphone/tablet) requires significant resources.
- It requires a different skill set compared to web application development.
- To ensure quality, you must use the official SDK of each platform, effectively developing the same app twice.
- Publishing apps on stores (App Store/Play Store) incurs costs, even for free software.
- The web interface is responsive, allowing quick access on mobile devices.
- Using the board on a small screen is not always practical.
