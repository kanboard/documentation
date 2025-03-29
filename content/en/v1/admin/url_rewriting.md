---
title: URL Rewriting
slug: url-rewriting
toc: true
menu:
    main:
        parent: Administration
---

Kanboard can work with or without URL rewriting enabled.

- Example of a rewritten URL: `/board/123`
- Without rewriting: `?controller=board&action=show&project_id=123`

If you use Kanboard with Apache and have the `mod_rewrite` module enabled, nice URLs will be used automatically. If you encounter a "404 Not Found" error, you may need to set the following overrides for your `DocumentRoot` to enable `.htaccess` files:

```sh
<Directory /var/www/kanboard/>
    AllowOverride FileInfo Options=All,MultiViews AuthConfig
</Directory>
```

### URL Shortcuts

- Go to task #123: **/t/123**
- Go to the board of project #2: **/b/2**
- Go to the project calendar #5: **/c/5**
- Go to the list view of project #8: **/l/8**
- Go to the project settings for project ID #42: **/p/42**

### Configuration

By default, Kanboard checks if Apache's `mod_rewrite` is enabled.

To disable automatic detection of URL rewriting, you can enable this feature manually in your `config.php` file:

```php
define('ENABLE_URL_REWRITE', true);
```

When this constant is set to `true`:

- URLs generated from command-line tools will also be rewritten.
- If you use a web server other than Apache (e.g., Nginx or Microsoft IIS), you must configure URL rewriting yourself.

Note: Kanboard always falls back to traditional URLs if URL rewriting is not configured. This configuration is optional.

### Nginx Configuration Example

In the `server` section of your Nginx configuration file, you can use the following example:

```bash
index index.php;

location / {
    try_files $uri $uri/ /index.php$is_args$args;

    # If Kanboard is under a subfolder
    # try_files $uri $uri/ /kanboard/index.php;
}

location ~ \.php$ {
    try_files $uri =404;
    fastcgi_split_path_info ^(.+\.php)(/.+)$;
    fastcgi_pass unix:/var/run/php5-fpm.sock;
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    fastcgi_index index.php;
    include fastcgi_params;
}

# Deny access to the data directory
location ~* /data {
    deny all;
    return 404;
}

# Deny access to .htaccess
location ~ /\.ht {
    deny all;
    return 404;
}
```

In your Kanboard `config.php`:

```php
define('ENABLE_URL_REWRITE', true);
```

Another example with Kanboard in a subfolder:

```nginx
server {
    listen 443 ssl default_server;
    listen [::]:443 ssl default_server;

    root /var/www/html;
    index index.php index.html index.htm;
    server_name _;

    location / {
        try_files $uri $uri/ =404;
    }

    location ^~ /kanboard {

        location /kanboard {
            try_files $uri $uri/ /kanboard/index.php$is_args$args;
        }

        location ~ ^/kanboard/(?:kanboard|config.php|config.default.php) {
            deny all;
        }

        location ~* /kanboard/data {
            deny all;
        }

        location ~ \.php(?:$|/) {
            fastcgi_split_path_info ^(.+\.php)(/.+)$;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
            fastcgi_param PATH_INFO $fastcgi_path_info;
            fastcgi_param HTTPS on; # Use only if HTTPS is configured
            include fastcgi_params;
            fastcgi_pass unix:/var/run/php5-fpm.sock;
        }

        location ~ /kanboard/\.ht {
            deny all;
        }
    }
}
```

Adapt the example above according to your configuration.

### Lighttpd Configuration Example

1. Enable `mod_rewrite`:

```bash
server.modules += (
    "mod_rewrite",
    ...
)
```

2. Add URL rewrites to the relevant sections of your `lighttpd.conf` (in this case, for host `example.com`). Keep the assets directory and the favicon static:

```bash
$HTTP["host"] == "example.com" {
  server.document-root = "/var/www/kanboard/"
  url.rewrite-once = (
    "^(/[^\?]*)(\?.*)?" => "/index.php$2",
    "^/assets/.+" => "$0",
    "^/favicon\.png$" => "$0",
  )
}
```

3. Reload the Lighttpd configuration:

```bash
/etc/init.d/lighttpd reload
```

### IIS Configuration Example

1. Download and install the Rewrite module for IIS: [Download link](http://www.iis.net/learn/extensions/url-rewrite-module/using-the-url-rewrite-module).
2. Create a `web.config` file in your installation folder:

```xml
<?xml version="1.0"?>
<configuration>
    <system.webServer>
        <defaultDocument>
            <files>
                <clear />
                <add value="index.php" />
            </files>
        </defaultDocument>
        <rewrite>
            <rules>
                <rule name="Kanboard URL Rewrite" stopProcessing="true">
                    <match url="^(.*)$" ignoreCase="false" />
                    <conditions logicalGrouping="MatchAll">
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" ignoreCase="false" negate="true" />
                    </conditions>
                    <action type="Rewrite" url="index.php" appendQueryString="true" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>
```

In your Kanboard `config.php`:

```php
define('ENABLE_URL_REWRITE', true);
```

Adapt the example above according to your configuration.
