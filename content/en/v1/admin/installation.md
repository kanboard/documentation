---
title: Installation Instructions
toc: true
menu:
    main:
        parent: Administration
aliases:
    - /en/latest/admin_guide/installation.html
    - /en/1.2.24/admin_guide/installation.html
    - /en/1.2.23/admin_guide/installation.html
    - /en/1.2.22/admin_guide/installation.html
    - /en/1.2.21/admin_guide/installation.html
    - /en/1.2.20/admin_guide/installation.html
---

{{< hint type="info" >}}
Check the list of [requirements]({{< relref "requirements.md" >}}) before proceeding.
{{</ hint >}}

{{< hint type="danger" >}}
- Change the default username/password.
- Prevent public access to the `data` directory via the URL.
- Enable `.htaccess` if you use Apache (Option `AllowOverride All`).
- It is your responsibility to configure your server correctly.
{{</ hint >}}

## From the Archive (Stable Version)

1. Ensure you have a web server with PHP installed.
2. Download the [source code](https://github.com/kanboard/kanboard/releases/latest) and copy the `kanboard` directory to your desired location.
3. Verify that the `data` directory is writable by the web server user.
4. Open your browser and navigate to `http://yourpersonalserver/kanboard`.
5. The default login and password are **admin/admin**.
6. Start using the software.
7. Don't forget to change your password!

The `data` folder is used to store:

- SQLite database: `db.sqlite`
- Debug file: `debug.log` (if debug mode is enabled with the `file` driver)
- Uploaded files: `files/*`
- Image thumbnails: `files/thumbnails/*`

If you are using a remote database (MySQL/PostgreSQL) and object storage (e.g., AWS S3), you may not need a persistent local `data` folder or to change its permissions.

## From the Git Repository (Development Version)

1. Clone the repository:

   ```bash
   git clone https://github.com/kanboard/kanboard.git
   ```

2. Follow step 3 from the archive installation instructions above.

{{< hint type="warning" >}}
This method installs the **current development version**. Use it at your own risk.
{{</ hint >}}
