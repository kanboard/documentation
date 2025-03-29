---
title: PostgreSQL
toc: true
menu:
    main:
        parent: Administration
---

By default, Kanboard uses SQLite to store its data, but it's also possible to use PostgreSQL.

## Requirements

- PostgreSQL >= 9.3
- The PHP extension `pdo_pgsql` installed (Debian/Ubuntu: `apt-get install php-pgsql`)

## Configuration

### Create an Empty Database

Run the following command in `psql`:

```sql
CREATE DATABASE kanboard;
```

### Create a Config File

The file `config.php` should contain the following values:

```php
<?php

// Use PostgreSQL instead of SQLite
define('DB_DRIVER', 'postgres');

// PostgreSQL parameters
define('DB_USERNAME', 'REPLACE_ME');
define('DB_PASSWORD', 'REPLACE_ME');
define('DB_HOSTNAME', 'REPLACE_ME');
define('DB_NAME', 'kanboard');
```

Note: You can also rename the template file `config.default.php` to `config.php`.

### Importing SQL Dump (Alternative Method)

When Kanboard is run for the first time, it will execute each database migration one by one. This process can take some time depending on your configuration.

To avoid potential issues or timeouts, you can initialize the database directly by importing the SQL schema:

```bash
psql -U postgres kanboard < app/Schema/Sql/postgres.sql
```

The file `app/Schema/Sql/postgres.sql` is a SQL dump that represents the latest version of the database.
