---
title: API Reference
linktitle: API
description: JSON-RPC API Reference
sectionToc: true
toc: true
menu:
    main:
        weight: 50
aliases:
    - /en/latest/api/index.html
---

Introduction
------------
There are two types of API access:

### Application API

- Access the API with the user "jsonrpc" and the token available on the settings page.
- Access all procedures.
- No permissions are checked.
- There is no user session on the server.
- No access to procedures that start with "My..." (e.g., "getMe" or "getMyProjects").
- Example of possible clients: tools to migrate/import data, create tasks from another system, etc.

### User API

- Access the API with user credentials (username and password).
- You can also generate a personal access token instead of your password.
- Application roles and project permissions are checked for each procedure.
- A user session is created on the server.
- Example of possible clients: native mobile/desktop applications, command-line utilities, etc.

Security
--------

- Always use HTTPS with a valid certificate (avoid clear-text communication).
- If you develop a mobile application, it\'s your responsibility to store user credentials securely on the device.
- After three authentication failures on the user API, the end-user must unlock their account using the login form.

{{< hint type="warning" >}}
Since Kanboard v1.2.8, users with two-factor authentication enabled must use API keys.
{{</ hint >}}

## Protocol

Kanboard uses the JSON-RPC protocol to interact with external programs.

JSON-RPC is a remote procedure call protocol encoded in JSON. It is similar to XML-RPC but uses the JSON format.

Kanboard use [version 2 of the protocol](http://www.jsonrpc.org/specification).
You must call the API with a `POST` HTTP request.

Kanboard supports batch requests, allowing you to make multiple API calls in a single HTTP request.
This is particularly useful for mobile clients with higher network latency.

## API Procedures
