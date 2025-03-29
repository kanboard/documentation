---
title: Background Workers
toc: true
menu:
    main:
        parent: Administration
---

{{< hint type="warning" >}}
This feature is no longer maintained. Use it at your own risk.
{{</ hint >}}

Depending on your configuration, some features can slow down the application if they are executed in the same process as the HTTP request. Kanboard can delegate these tasks to a background worker that listens for incoming events.

Examples of features that may slow down Kanboard:

- Sending emails via an external SMTP server can take several seconds.
- Sending notifications to external services.

This feature is optional and requires the installation of a queue daemon on your server.

## Beanstalk

[Beanstalk](http://kr.github.io/beanstalkd/) is a simple, fast work queue.

- Install Beanstalk using the package manager of your Linux distribution.
- Install the [Kanboard plugin for Beanstalk](https://github.com/kanboard/plugin-beanstalk).
- Start the worker with the Kanboard command-line tool: `./cli worker`.

## RabbitMQ

[RabbitMQ](https://www.rabbitmq.com/) is a robust messaging system suitable for high-availability infrastructure.

- Follow the official RabbitMQ documentation for installation and configuration.
- Install the [Kanboard plugin for RabbitMQ](https://github.com/kanboard/plugin-rabbitmq).
- Start the worker with the Kanboard command-line tool: `./cli worker`.

## Notes

- Start the Kanboard worker with a process supervisor (e.g., systemd, upstart, or supervisord).
- Ensure the process has access to the data folder if you store files on the local filesystem or use SQLite.
