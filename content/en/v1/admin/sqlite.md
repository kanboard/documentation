---
title: SQLite
toc: true
menu:
    main:
        parent: Administration
---

Kanboard uses SQLite by default to store its data. All tasks, projects, and users are stored inside this database.

Technically, the database is a single file located inside the `data` directory and named `db.sqlite`.

## DB Exportation

### Command Line

Creating a backup is very easy. Simply copy the file `data/db.sqlite` to another location when no one is using the software.

If you want to create a backup while users are connected, you can use `sqlite3` to create the backup.

- Dump the database to a text file of SQL commands: `sqlite3 db.sqlite .dump > kanboard.dump.sql`
- Create a backup in SQLite format: `sqlite3 db.sqlite ".backup kanboard.backup.sqlite"`

### User Interface

You can also download the database at any time directly from the **Settings** menu.

The downloaded database is compressed with Gzip, and the filename becomes `db.sqlite.gz`.

## DB Importation

Currently, there is no way to restore the database from the user interface. Restoration must be done manually when no one is using the software.

- To restore an old backup, replace and overwrite the existing file `data/db.sqlite`.
- To uncompress a gzipped database, execute this command from a terminal: `gunzip db.sqlite.gz`.
- To restore a backup in SQL format: `sqlite3 db.sqlite < kanboard.dump.sql` (ensure `db.sqlite` does not already exist).
- To restore a backup in SQLite format: `sqlite3 db.sqlite ".restore kanboard.backup.sqlite"`

## Optimization

Occasionally, you can optimize the database file by running the `VACUUM` command. This command rebuilds the entire database and can be used for several reasons:

- Reduce the file size: Deleting data creates empty space but does not reduce the file size.
- Defragment the database due to frequent inserts or updates.

### From the Command Line

```bash
sqlite3 data/db.sqlite 'VACUUM'
```

### From the User Interface

Go to the **Settings** menu and click on the link **Optimize the database**.

For more information, read the [SQLite documentation](https://sqlite.org/lang_vacuum.html).

## Notes

- Since Kanboard v1.2.27, [WAL mode](https://www.sqlite.org/wal.html) is enabled by default. To disable this feature, set the value of `DB_WAL_MODE` to `false`.
