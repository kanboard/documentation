---
title: Performance Optimization
toc: true
menu:
    main:
        parent: Administration
---

Depending on your configuration, some features can slow down Kanboard. By default, all operations are synchronous and performed in the same thread as the HTTP request. This is a PHP limitation. However, it's possible to improve performance.

Depending on the plugins you install, communicating with external services can take hundreds of milliseconds or even seconds. To avoid blocking the main thread, you can delegate these operations to a pool of background workers. This setup requires additional software in your infrastructure.

## How to Detect Bottlenecks

- Enable debug mode.
- Monitor the log file.
- Perform an action in Kanboard (e.g., drag and drop a task).
- All operations are logged with their execution time (HTTP requests, email notifications, SQL queries).

## Improve Email Notification Speed

Using the SMTP method with an external server can be very slow.

Possible solutions:

- Use background workers if you still want to use SMTP.
- Use a local email relay with Postfix and the "mail" transport.
- Use an email provider that supports an HTTP API to send emails (e.g., Sendgrid, Mailgun, or Postmark).

## Improve SQLite Performance

Possible solutions:

- Do not use SQLite when you have a lot of concurrency (several users). Choose PostgreSQL or MySQL instead.
- Do not use SQLite on a shared NFS mount.
- Do not use SQLite on a disk with poor IOPS. It is always preferable to use local SSD drives.
