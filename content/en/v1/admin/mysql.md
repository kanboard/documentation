---
title: MySQL/MariaDB
toc: true
menu:
    main:
        parent: Administration
---

By default, Kanboard uses SQLite to store its data. However, it's possible to use MySQL or MariaDB instead of SQLite.

## Requirements

- MySQL >= 5.6 or MariaDB >= 10
- The PHP extension `pdo_mysql` installed

## MySQL Configuration

### Create a Database

The first step is to create a database on your MySQL server. For example, you can do this from the MySQL client:

```sql
CREATE DATABASE kanboard CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

{{< hint type="info" >}}
Since version 1.2.3, Kanboard uses the utf8mb4 encoding instead of utf8.
{{</ hint >}}

You can then assign the required permissions on the database:

```sql
GRANT ALTER, CREATE, DELETE, DROP, INDEX, INSERT, REFERENCES, SELECT, UPDATE, LOCK TABLES ON kanboard.* TO 'USERNAME'@'HOST' IDENTIFIED BY 'PASSWORD';
```

### Create a Config File

The file `config.php` should contain these values:

```php
<?php

// Use MySQL instead of SQLite
define('DB_DRIVER', 'mysql');

// MySQL parameters
define('DB_USERNAME', 'REPLACE_ME');
define('DB_PASSWORD', 'REPLACE_ME');
define('DB_HOSTNAME', 'REPLACE_ME');
define('DB_NAME', 'kanboard');
```

Note: You can also rename the template file `config.default.php` to `config.php`.

### Importing SQL Dump (Alternative Method)

When Kanboard is run for the first time, it will execute each database migration one by one. This process can take some time depending on your configuration.

To avoid potential timeouts, you can initialize the database directly by importing the SQL schema:

```bash
mysql -u root -p kanboard < app/Schema/Sql/mysql.sql
```

The file `app/Schema/Sql/mysql.sql` is a SQL dump that represents the latest version of the database.

If you would like to use a Unix socket connection, try this:

```php
define('DB_HOSTNAME', '127.0.0.1;unix_socket=/var/run/mysqld/mysqld.sock');
```

## SSL Configuration

These parameters must be defined to enable the MySQL SSL connection:

```php
// MySQL SSL key
define('DB_SSL_KEY', '/path/to/client-key.pem');

// MySQL SSL certificate
define('DB_SSL_CERT', '/path/to/client-cert.pem');

// MySQL SSL CA
define('DB_SSL_CA', '/path/to/ca-cert.pem');
```
````
