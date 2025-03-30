---
title: Plugin Schema Migrations
toc: true
menu:
    main:
        parent: Developing Plugins
---

Kanboard executes database migrations automatically for you. Migrations must be stored in a folder named **Schema**, and the filename must match the database driver:

```bash
Schema
├── Mysql.php
├── Postgres.php
└── Sqlite.php
```

Each file contains all migrations. Here is an example for Sqlite:

```php
<?php

namespace Kanboard\Plugin\Something\Schema;

const VERSION = 1;

function version_1($pdo)
{
    $pdo->exec('CREATE TABLE IF NOT EXISTS something (
        "id" INTEGER PRIMARY KEY,
        "project_id" INTEGER NOT NULL,
        "something" TEXT,
        FOREIGN KEY(project_id) REFERENCES projects(id) ON DELETE CASCADE
    )');
}
```

- The constant `VERSION` represents the latest version of your schema.
- Each function corresponds to a migration, e.g., `version_1()`, `version_2()`, etc.
- A `PDO` instance is passed as the first argument.
- All migrations are executed within a transaction. If an error occurs, a rollback is performed, and the error is displayed to the user.

Kanboard compares the version defined in your schema with the version stored in the database. If the versions differ, Kanboard executes each migration sequentially until the latest version is reached.
