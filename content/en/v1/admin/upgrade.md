---
title: Upgrading to a New Version
toc: true
menu:
    main:
        parent: Administration
aliases:
    - /en/latest/admin_guide/upgrade.html
    - /en/1.2.24/admin_guide/upgrade.html
    - /en/1.2.23/admin_guide/upgrade.html
    - /en/1.2.22/admin_guide/upgrade.html
    - /en/1.2.21/admin_guide/upgrade.html
    - /en/1.2.20/admin_guide/upgrade.html
---

{{< hint type="warning" >}}
Do not update the software blindly without reading the [ChangeLog](https://github.com/kanboard/kanboard/blob/master/ChangeLog). Always check for breaking changes.
{{</ hint >}}

Most of the time, upgrading Kanboard to a newer version is seamless. The process can be summarized as simply copying your `data` folder to the new Kanboard folder. Kanboard will automatically run database migrations for you.

## Important Steps Before Updating

- **Always make a backup of your data before upgrading.**
- **Verify that your backup is functional.**
- Read the [ChangeLog](https://github.com/kanboard/kanboard/blob/master/ChangeLog) and check for breaking changes.
- Stop the worker if you are using it.
- Put the web server in maintenance mode to prevent users from accessing the software during the upgrade.
- Flush all user sessions (truncate the `sessions` table in the database).

## From the Archive (Stable Version)

1. Decompress the new archive.
2. Copy the `data` folder into the newly uncompressed directory.
3. Copy your custom `config.php` file, if applicable.
4. If you have installed plugins, ensure you use their latest versions.
5. Verify that the `data` directory is writable by your web server user.
6. Modify `.htaccess` if needed (e.g., to enforce SSL).
7. Test the installation.
8. Remove your old Kanboard directory.

## From the Repository (Development Version)

1. Run `git pull`.
2. Log in and verify that everything is functioning correctly.

- This method installs the **current development version**. Use it at your own risk.
- Do not update the software blindly without checking the [ChangeLog](https://github.com/kanboard/kanboard/blob/master/ChangeLog).

## Running SQL Migrations Manually

By default, SQL migrations are executed automatically. The schema version is checked at each request. This ensures that when you upgrade Kanboard, the database schema is updated for you. However, this method **is not perfect**.

- **Ensure only one process accesses the database while running migrations.**
- Put your Kanboard instance in "maintenance mode" to prevent users from accessing the software while altering the database schema.

To run database migrations manually, set the parameter `DB_RUN_MIGRATIONS` to `false` in your config file.

When upgrading Kanboard, run this command:

```bash
./cli db:migrate
```
