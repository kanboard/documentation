---
title: Automated Tests
toc: true
menu:
    main:
        parent: Contributing to Kanboard
---

[PHPUnit](https://phpunit.de/) is used to run automated tests on Kanboard.

Tests can be run across different databases (Sqlite, MySQL, and PostgreSQL) to ensure consistent results.

## Requirements

- Linux/Unix machine
- PHP
- PHPUnit installed
- MySQL and PostgreSQL (optional)
- Selenium (optional)
- Firefox (optional)

## Unit Tests

### Testing with Sqlite

Sqlite tests use an in-memory database, so nothing is written to the file system.

The PHPUnit config file is `tests/units.sqlite.xml`. Run the following command from your Kanboard directory:

```bash
phpunit -c tests/units.sqlite.xml
```

Example output:

```bash
PHPUnit 5.0.0 by Sebastian Bergmann and contributors.

...............................................................  63 / 649 (  9%)
............................................................... 126 / 649 ( 19%)
............................................................... 189 / 649 ( 29%)
............................................................... 252 / 649 ( 38%)
............................................................... 315 / 649 ( 48%)
............................................................... 378 / 649 ( 58%)
............................................................... 441 / 649 ( 67%)
............................................................... 504 / 649 ( 77%)
............................................................... 567 / 649 ( 87%)
............................................................... 630 / 649 ( 97%)
...................                                             649 / 649 (100%)

Time: 1.22 minutes, Memory: 151.25Mb

OK (649 tests, 43595 assertions)
```

### Testing with MySQL

Ensure MySQL or MariaDB is installed on localhost. Default credentials:

- Hostname: **localhost**
- Username: **root**
- Password: none
- Database: **kanboard_unit_test**

The database is dropped and recreated for each execution. Use the config file `tests/units.mysql.xml`:

```bash
phpunit -c tests/units.mysql.xml
```

### Testing with PostgreSQL

Ensure PostgreSQL is installed on localhost. Default credentials:

- Hostname: **localhost**
- Username: **postgres**
- Password: none
- Database: **kanboard_unit_test**

The database is recreated for each execution. Use the config file `tests/units.postgres.xml`:

```bash
phpunit -c tests/units.postgres.xml
```

## Integration Tests

Integration tests primarily test the API by making real HTTP calls to the application running inside a container.

### Requirements

- PHP
- Composer
- Unix operating system (Mac OS or Linux)
- Docker
- Docker Compose

### Running Integration Tests

Integration tests use Docker containers. Commands to run tests:

```bash
# Run tests with Sqlite
make integration-test-sqlite

# Run tests with MySQL
make integration-test-mysql

# Run tests with PostgreSQL
make integration-test-postgres
```

## Acceptance Tests

Acceptance tests (also known as end-to-end or functional tests) test the UI functionality in a browser using Selenium.

### Requirements

- [Selenium Standalone Server](http://www.seleniumhq.org/download/)
- Compatible version of Firefox

Run the tests using the config file `tests/acceptance.xml`:

```bash
make test-browser
```

Example output:

```bash
$ make test-browser
PHPUnit 4.8.26 by Sebastian Bergmann and contributors.

..

Time: 5.59 seconds, Memory: 5.25MB

OK (2 tests, 5 assertions)
```
