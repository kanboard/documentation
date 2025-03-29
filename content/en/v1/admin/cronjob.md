---
title: Cronjob Configuration
toc: true
menu:
    main:
        parent: Administration
---

To work properly, Kanboard requires a background job to run on a daily basis. Usually, on Unix platforms, this process is handled by `cron`.

This background job is necessary for the following features:

- Reports and analytics (calculate daily stats for each project)
- Sending overdue task notifications
- Executing automatic actions connected to the event "Daily background job for tasks"

## Configuration on Unix and Linux Platforms

There are multiple ways to define a cronjob on Unix/Linux operating systems. The following example is for Ubuntu 14.04. The procedure is similar for other systems.

Edit the crontab of your web server user:

```bash
sudo crontab -u www-data -e
```

Example to execute the daily cronjob at 8 AM:

```bash
0 8 * * * cd /path/to/kanboard && ./cli cronjob >/dev/null 2>&1
```

**Note:** The cronjob process must have write access to the database if you are using SQLite. Usually, running the cronjob under the web server user is sufficient.

## Configuration on Microsoft Windows Server

Before configuring the recurring task, create a batch file (`*.bat` or `*.cmd`) to run the Kanboard CLI script.

Here is an example (`C:\kanboard.bat`):

```cmd
"C:\php\php.exe" -f "C:\inetpub\wwwroot\kanboard\cli" cronjob
```

**You must change the path of the PHP executable and the path of Kanboard's script according to your installation.**

### Configure the Windows Task Scheduler

1. Go to "Administrative Tools."
2. Open the "Task Scheduler."
3. On the right, choose "Create Task."
4. Choose a name, for example, "Kanboard."
5. Under "Security Options," choose a user that can write to the database if you are using SQLite (this might be `IIS_IUSRS` depending on your configuration).
6. Create a new "Trigger," choose "Daily," and set a time (e.g., midnight).
7. Add a new action, choose "Start a program," and select the batch file created above.

## Configuration by Calling a URL

If your hosting provider does not offer CLI access, you can run cron jobs by calling a URL. The URL is protected using the webhook token and should be called via HTTPS for added security.

### Cron Job URL

Without URL rewriting:

```plaintext
https://domain.tld/?controller=CronjobController&action=run&token=WEBHOOK_TOKEN_HERE
```

With URL rewriting enabled:

```plaintext
https://domain.tld/cronjob?token=WEBHOOK_TOKEN_HERE
```
