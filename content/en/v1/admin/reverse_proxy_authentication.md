---
title: Reverse Proxy Authentication
toc: true
menu:
    main:
        parent: Administration
---

This authentication method is often used for [SSO](http://en.wikipedia.org/wiki/Single_sign-on) (Single Sign-On), especially for large organizations.

The authentication is handled by another system.
Kanboard does not store your password and assumes you are already authenticated.

## Requirements

- Apache or another web server with authentication capabilities (e.g., Basic Auth, LDAP, OAuth, SAML)
- A reverse proxy configured to authenticate users and forward authentication headers to Kanboard
- Network configuration ensuring Kanboard is only accessible through the reverse proxy

## How Does This Work?

1. Your reverse proxy authenticates the user and sends the username through an HTTP header.
2. Kanboard retrieves the username from the request:
    - The user is created automatically if necessary.
    - A new Kanboard session is opened without any prompt, assuming the authentication is valid.

## Installation Instructions

### Setting Up Your Reverse Proxy

This is outside the scope of this documentation. You must configure your reverse proxy to authenticate users and pass the authenticated username via an HTTP header to Kanboard.

Consult your reverse proxy documentation to:

- Enable authentication (e.g., Basic Auth, LDAP, OAuth, SAML)
- Configure the proxy to set an HTTP header containing the authenticated username
- Identify which header name your proxy uses (e.g., `REMOTE_USER`, `X-Forwarded-User`, `X-Authenticated-User`)

You will need this header name for the Kanboard configuration below.

#### Security (important): prevent authentication header spoofing

When reverse proxy authentication is enabled, Kanboard trusts the configured header (for example `REMOTE_USER` or `HTTP_X_AUTHENTICATED_USER`).
If an attacker can reach Kanboard directly (bypassing the reverse proxy) or can inject headers that your proxy forwards, they could impersonate another user.

To avoid this, configure your reverse proxy so that:

- Kanboard is not reachable directly from untrusted networks (only through the reverse proxy).
- The proxy removes any incoming authentication headers from the client request.
- The proxy sets the authentication header itself, using a value coming from the proxy authentication step.

Nginx example (strip client-supplied headers, then set your own):

```nginx
location / {
    # Strip any client-supplied authentication headers to prevent spoofing
    proxy_set_header X-Forwarded-User "";
    proxy_set_header REMOTE_USER "";

    # Set the authentication header from the authenticated user
    # For HTTP Basic Auth, use $remote_user
    proxy_set_header X-Forwarded-User $remote_user;

    # For auth_request module, use a variable from your auth subrequest:
    # proxy_set_header X-Forwarded-User $auth_user;

    # Forward other standard headers
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;

    proxy_pass http://kanboard_upstream;
}
```

Apache example (unset, then set from the authenticated user):

```apache
# Strip any client-supplied authentication headers to prevent spoofing
RequestHeader unset X-Forwarded-User
RequestHeader unset REMOTE_USER

# Set the authentication header from the authenticated user
# This example assumes Apache HTTP Basic Auth or similar module
RequestHeader set X-Forwarded-User "%{REMOTE_USER}e"

# Alternative: if using mod_auth_openidc or similar OAuth/OIDC module:
# RequestHeader set X-Forwarded-User "%{OIDC_CLAIM_preferred_username}e"
```

Also ensure the upstream Kanboard server only accepts connections from the reverse proxy (for example, firewall rules, binding Kanboard to `127.0.0.1`, or allowing only the proxy IP).

### Setting Up Kanboard

Since Kanboard version 1.2.49, it is mandatory to configure the `TRUSTED_PROXY_NETWORKS` option when enabling reverse proxy authentication.
This setting specifies the list of trusted proxy networks in CIDR format that are permitted to set the authentication header.

For instance, if your reverse proxy operates on the same server as Kanboard, you can configure it as follows: `127.0.0.1/32,::1/128`.

```php
define('TRUSTED_PROXY_NETWORKS', '127.0.0.1/32,::1/128');
```

Then, enable reverse proxy authentication by adding the following configuration to your `config.php` file.

```php
// Enable/disable reverse proxy authentication
define('REVERSE_PROXY_AUTH', true); // Set this value to true

// The HTTP header to retrieve. If not specified, REMOTE_USER is the default
define('REVERSE_PROXY_USER_HEADER', 'REMOTE_USER');

// The default Kanboard admin for your organization.
// Since everything should be filtered by the reverse proxy,
// you may want to have a bootstrap admin user.
define('REVERSE_PROXY_DEFAULT_ADMIN', 'myadmin');

// The default domain to assume for the email address.
// If the username is not an email address, it
// will be updated automatically as USER@mydomain.com
define('REVERSE_PROXY_DEFAULT_DOMAIN', 'mydomain.com');

// Header name to use for the user email (optional)
define('REVERSE_PROXY_EMAIL_HEADER', 'REMOTE_EMAIL');

// Header name to use for the user full name (optional)
define('REVERSE_PROXY_FULLNAME_HEADER', 'REMOTE_NAME');
```

#### Custom Header Names

If you want to use a custom HTTP header for `REVERSE_PROXY_USER_HEADER` option, you must follow PHP's `$_SERVER` variable naming convention:

1. Prefix the header name with `HTTP_`
2. Convert to uppercase
3. Replace hyphens with underscores

**Examples:**

- `X-Proxy-Username` → `HTTP_X_PROXY_USERNAME`
- `X-Authenticated-User` → `HTTP_X_AUTHENTICATED_USER`

**Note:** The standard `REMOTE_USER` header is an exception and does not require the `HTTP_` prefix.
