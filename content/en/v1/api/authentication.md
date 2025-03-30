---
title: API Authentication
toc: true
menu:
    main:
        parent: API Reference
---

{{< hint type="warning" >}}
Since Kanboard v1.2.8, people with two-factor authentication enabled must use API keys.
{{</ hint >}}

API endpoint
------------

URL: `https://YOUR_SERVER/jsonrpc.php`

Default method (HTTP Basic)
---------------------------

### Application credentials

- Username: `jsonrpc`
- Password: API token on the settings page

### User credentials

- Username: username
- Password: user password or personal access token

The API use the [HTTP Basic Authentication Scheme described in the
RFC2617](http://www.ietf.org/rfc/rfc2617.txt).

Custom HTTP header
------------------

You can use an alternative HTTP header for authentication if your server has a very specific configuration.

- The header name can be anything, for example, `X-API-Auth`.
- The header value is the `username:password` encoded in Base64.

Configuration:

1. Define your custom header in your `config.php`: `define('API_AUTHENTICATION_HEADER', 'X-API-Auth');`
2. Encode the credentials in Base64. Example with PHP: `base64_encode('jsonrpc:19ffd9709d03ce50675c3a43d1c49c1ac207f4bc45f06c5b2701fbdf8929');`
3. Test with curl:

```bash
curl \
-H 'X-API-Auth: anNvbnJwYzoxOWZmZDk3MDlkMDNjZTUwNjc1YzNhNDNkMWM0OWMxYWMyMDdmNGJjNDVmMDZjNWIyNzAxZmJkZjg5Mjk=' \
-d '{"jsonrpc": "2.0", "method": "getAllProjects", "id": 1}' \
http://localhost/kanboard/jsonrpc.php
```

Authentication error
--------------------

If the credentials are wrong, you will receive a `401 Not Authorized`
and the corresponding JSON response.

Authorization error
-------------------

If the connected user is not allowed to access to the resource, you will
receive a `403 Forbidden`.
