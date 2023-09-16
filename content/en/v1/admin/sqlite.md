---
title: Sqlite
toc: true
---

Kanboard uses Sqlite by default to store its data.
All tasks, projects and users are stored inside this database.

Technically, the database is just a single file located inside the directory `data` and named `db.sqlite`.

Export/Backup
-------------

### Command line

Doing a backup is very easy, just copy the file `data/db.sqlite`
somewhere else when nobody use the software.

If you want to do a backup while users are connected, you can use `sqlite3` to create the backup.

- You can dump the database to a text file of sql commands like this: `sqlite3 db.sqlite .dump > kanboard.dump.sql`
- Another option is to create a backup in sqlite format: `sqlite3 db.sqlite ".backup kanboard.backup.sqlite"`

### User interface

You can also download at any time the database directly from the **Settings** menu.

The downloaded database is compressed with Gzip, the filename becomes `db.sqlite.gz`.

Import/Restoration
------------------

There is actually no way to restore the database from the user
interface. The restoration must be done manually when no body use the
software.

- To restore an old backup, just replace and overwrite the actual file `data/db.sqlite`.
- To uncompress a gzipped database, execute this command from a terminal `gunzip db.sqlite.gz`.
- A backup in sql format, can be restored like this: `sqlite3 db.sqlite < kanboard.dump.sql` (db.sqlite must not exist)
- A backup in sqlite format, can be restored like this: `sqlite3 db.sqlite ".restore kanboard.backup.sqlite"`

Optimization
------------

Occasionally, it's possible to optimize the database file by running the
command `VACUUM`. This command rebuild the entire database and can be
used for several reasons:

- Reduce the file size, deleting data produce empty space but doesn't change the file size.
- The database is fragmented due to frequent inserts or updates.

### From the command line

    sqlite3 data/db.sqlite 'VACUUM'

### From the user interface

Go to the **Settings** menu and click on the link **Optimize the
database**.

For more information, read the [Sqlite documentation](https://sqlite.org/lang_vacuum.html).

Notes
-----

- Since Kanboard v1.2.27, [WAL mode](https://www.sqlite.org/wal.html) is enabled by default. If you would like to disable this feature, change the value of `DB_WAL_MODE` to `false`.
