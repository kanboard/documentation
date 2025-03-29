---
title: LDAP Configuration Parameters
toc: true
menu:
    main:
        parent: Administration
---

## Requirements

- PHP LDAP extension enabled
- LDAP server:
    - OpenLDAP
    - Microsoft Active Directory
    - Novell eDirectory

## LDAP Authentication

### Workflow

When LDAP authentication is activated, the login process works as follows:

1. Kanboard first tries to authenticate the user using the database.
2. If the user is not found in the database, LDAP authentication is performed.
3. If LDAP authentication is successful, a local user is created automatically (by default) with no password and marked as an LDAP user.

The full name and email address are automatically fetched from the LDAP server.

### Authentication Types

| Type       | Description                                              |
|------------|----------------------------------------------------------|
| Proxy User | A specific user is used to browse the LDAP directory.    |
| User       | The end-user credentials are used for browsing LDAP.     |
| Anonymous  | No authentication is performed for LDAP browsing.        |

{{< hint type="info" >}}
The recommended authentication method is `Proxy`.
{{</ hint >}}

#### Anonymous Mode

```php
define('LDAP_BIND_TYPE', 'anonymous');
define('LDAP_USERNAME', null);
define('LDAP_PASSWORD', null);
```

This is the default value, but some LDAP servers don't allow anonymous browsing for security reasons.

#### Proxy Mode

A specific user is used to browse the LDAP directory:

```php
define('LDAP_BIND_TYPE', 'proxy');
define('LDAP_USERNAME', 'my proxy user');
define('LDAP_PASSWORD', 'my proxy password');
```

#### User Mode

This method uses the credentials provided by the end-user.

For example, Microsoft Active Directory doesn't allow anonymous browsing by default. If you don't want to use a proxy user, you can use this method.

```php
define('LDAP_BIND_TYPE', 'user');
define('LDAP_USERNAME', '%s@kanboard.local');
define('LDAP_PASSWORD', null);
```

In this case, the constant `LDAP_USERNAME` is used as a pattern for the LDAP username. Examples:

- `%s@kanboard.local` will be replaced by `my_user@kanboard.local`.
- `KANBOARD\\%s` will be replaced by `KANBOARD\my_user`.

### User LDAP Filter

The configuration parameter `LDAP_USER_FILTER` is used to find users in the LDAP directory.

Examples:

- `(&(objectClass=user)(sAMAccountName=%s))` is replaced by `(&(objectClass=user)(sAMAccountName=my_username))`.
- `uid=%s` is replaced by `uid=my_username`.

Other examples of [filters for Active Directory](http://social.technet.microsoft.com/wiki/contents/articles/5392.active-directory-ldap-syntax-filters.aspx).

Example to filter access to Kanboard:

`(&(objectClass=user)(sAMAccountName=%s)(memberOf=CN=Kanboard Users,CN=Users,DC=kanboard,DC=local))`

This example allows only members of the group "Kanboard Users" to connect to Kanboard.

### Example for Microsoft Active Directory

Let's say we have a domain `KANBOARD` (kanboard.local) and the primary controller is `myserver.kanboard.local`.

First example with proxy mode:

```php
<?php

// Enable LDAP authentication (false by default)
define('LDAP_AUTH', true);

define('LDAP_BIND_TYPE', 'proxy');
define('LDAP_USERNAME', 'administrator@kanboard.local');
define('LDAP_PASSWORD', 'my super secret password');

// LDAP server hostname
define('LDAP_SERVER', 'myserver.kanboard.local');

// LDAP properties
define('LDAP_USER_BASE_DN', 'CN=Users,DC=kanboard,DC=local');
define('LDAP_USER_FILTER', '(&(objectClass=user)(sAMAccountName=%s))');
```

Second example with user mode:

```php
<?php

// Enable LDAP authentication (false by default)
define('LDAP_AUTH', true);

define('LDAP_BIND_TYPE', 'user');
define('LDAP_USERNAME', '%s@kanboard.local');
define('LDAP_PASSWORD', null);

// LDAP server hostname
define('LDAP_SERVER', 'myserver.kanboard.local');

// LDAP properties
define('LDAP_USER_BASE_DN', 'CN=Users,DC=kanboard,DC=local');
define('LDAP_USER_FILTER', '(&(objectClass=user)(sAMAccountName=%s))');
```

### Example for OpenLDAP

Our LDAP server is `myserver.example.com`, and all users are stored under `ou=People,dc=example,dc=com`.

For this example, we use anonymous binding.

```php
<?php

// Enable LDAP authentication (false by default)
define('LDAP_AUTH', true);

// LDAP server hostname
define('LDAP_SERVER', 'myserver.example.com');

// LDAP properties
define('LDAP_USER_BASE_DN', 'ou=People,dc=example,dc=com');
define('LDAP_USER_FILTER', 'uid=%s');
```

### Example for LDAPS (SSL Encryption)

Some LDAP servers are configured for "LDAPS" connectivity only (on port 636). This is different from TLS, which starts in cleartext (port 389 by default) and then sets up encryption over the same channel.

To tell PHP to use LDAPS, you need to prefix the name of your LDAP server with `<ldaps://>`, as in the example below:

Our LDAP server is `myserver.example.com` and is only accessible via LDAPS. Most likely, we won't want to validate the server certificate, and we DON'T want TLS.

For this example, we use anonymous binding.

```php
<?php

// Enable LDAP authentication (false by default)
define('LDAP_AUTH', true);

// LDAP server hostname
define('LDAP_SERVER', 'ldaps://myserver.example.com');

// By default, require certificate to be verified for ldaps:// style URL. Set to false to skip the verification
define('LDAP_SSL_VERIFY', false);

// Enable LDAP START_TLS
define('LDAP_START_TLS', false);
```

### Disable Automatic Account Creation

By default, Kanboard will create a user account automatically if nothing is found.

You can disable this behavior if you prefer to create user accounts manually to restrict Kanboard to only some people.

Change the value of `LDAP_USER_CREATION` to `false`:

```php
// Automatically create user account
define('LDAP_USER_CREATION', false);
```

### Synchronization

By default, Kanboard will synchronize all fields (role, name, email...) except the username.

If you would like to change this behavior, use this config parameter:

```php
// This example will not synchronize the fields "username" and "role" from LDAP to Kanboard.
define('EXTERNAL_AUTH_EXCLUDE_FIELDS', 'username,role');
```

### Troubleshooting

#### SELinux Restrictions

If SELinux is enabled, you have to allow Apache to reach out to your LDAP server.

- You can switch SELinux to the permissive mode or disable it (not recommended).
- You can allow all network connections, for example: `setsebool -P httpd_can_network_connect=1`, or have a more restrictive rule.

In any case, refer to the official Redhat/Centos documentation.

#### Debug Mode

If you are not able to set up LDAP authentication correctly, you can enable debug mode and watch log files.

LDAP Group Synchronization
--------------------------

{{< hint type="info" >}}
Nested groups are not implemented.
{{</ hint >}}

### Requirements

- Have LDAP authentication properly configured
- Use a LDAP server that supports `memberOf` or `memberUid` (PosixGroups)

### Define automatically user roles based on LDAP groups

Use these constants in your config file:

- `LDAP_GROUP_ADMIN_DN`: Distinguished names for application
    administrators
- `LDAP_GROUP_MANAGER_DN`: Distinguished names for application
    managers

#### Example for Active Directory:

```php
define('LDAP_GROUP_ADMIN_DN', 'CN=Kanboard Admins,CN=Users,DC=kanboard,DC=local');
define('LDAP_GROUP_MANAGER_DN', 'CN=Kanboard Managers,CN=Users,DC=kanboard,DC=local');
```

- People member of "Kanboard Admins" will have the role "Administrator"
- People member of "Kanboard Managers" will have the role "Managers"
- Everybody else will have the role "User"

#### Example for OpenLDAP with Posix Groups:

```php
define('LDAP_GROUP_BASE_DN', 'ou=Groups,dc=kanboard,dc=local');
define('LDAP_GROUP_USER_FILTER', '(&(objectClass=posixGroup)(memberUid=%s))');
define('LDAP_GROUP_ADMIN_DN', 'cn=Kanboard Admins,ou=Groups,dc=kanboard,dc=local');
define('LDAP_GROUP_MANAGER_DN', 'cn=Kanboard Managers,ou=Groups,dc=kanboard,dc=local');
```

You **must define the parameter** `LDAP_GROUP_USER_FILTER` if your LDAP server use `memberUid` instead of `memberOf`. All parameters of this example are mandatory.

### Automatically load LDAP groups for project permissions

This feature allows you to sync automatically LDAP groups with Kanboard
groups. Each group can have a different project role assigned.

On the project permissions page, people can enter groups in the
auto-complete field and Kanboard can search for groups with any provider
enabled.

If the group doesn't exist in the local database, it will be
automatically synced.

- `LDAP_GROUP_PROVIDER`: Enable the LDAP group provider
- `LDAP_GROUP_BASE_DN`: Distinguished names to find groups in LDAP directory
- `LDAP_GROUP_FILTER`: LDAP filter used to perform the query
- `LDAP_GROUP_ATTRIBUTE_NAME`: LDAP attribute used to fetch the group name

#### Example for Active Directory:

```php
define('LDAP_GROUP_PROVIDER', true);
define('LDAP_GROUP_BASE_DN', 'CN=Groups,DC=kanboard,DC=local');
define('LDAP_GROUP_FILTER', '(&(objectClass=group)(sAMAccountName=%s*))');
```

With the filter given as example above, Kanboard will search for groups that match the query. If the end-user enter the text "My group" in the auto-complete box, Kanboard will return all groups that match the pattern: `(&(objectClass=group)(sAMAccountName=My group*))`.

- Note 1: The special characters `*` is important here, **otherwise an exact match will be done**.
- Note 2: This feature is only compatible with LDAP authentication configured in "proxy" or "anonymous" mode

[More examples of LDAP filters for Active Directory](http://social.technet.microsoft.com/wiki/contents/articles/5392.active-directory-ldap-syntax-filters.aspx)

#### Example for OpenLDAP with Posix Groups:

```php
define('LDAP_GROUP_PROVIDER', true);
define('LDAP_GROUP_BASE_DN', 'ou=Groups,dc=kanboard,dc=local');
define('LDAP_GROUP_FILTER', '(&(objectClass=posixGroup)(cn=%s*))');
```

LDAP User Profile Photo
-----------------------


Kanboard can download automatically user pictures from the LDAP server.

This feature is enabled only if LDAP authentication is activated and the parameter `LDAP_USER_ATTRIBUTE_PHOTO` is defined.

In your `config.php`, you have to set the LDAP attribute used to store the image.

```php
define('LDAP_USER_ATTRIBUTE_PHOTO', 'jpegPhoto');
```

Usually, the attributes `jpegPhoto` or `thumbnailPhoto` are used. The image can be stored in JPEG or PNG format.

To upload the image in the user profile, Active Directory administrators may use software like [AD Photo
Edit](http://www.cjwdev.co.uk/Software/ADPhotoEdit/Info.html).

{{< hint type="info" >}}
The profile image is **downloaded at login time only if the user do not already have uploaded an image previously**.

To change the user photo, the previous one have to be removed manually in the user profile.
{{</ hint >}}

LDAP Configuration Parameters
-----------------------------

{{< hint type="info" >}}
- LDAP attributes must be lowercase.
- Nested groups are not implemented.
{{</ hint >}}

Parameter                       | Default value | Description
--------------------------------| --------------| -----------------------------------------------
`LDAP_AUTH`                     | `false`         | Enable LDAP authentication
`LDAP_SERVER`                   | Empty         | LDAP server hostname
`LDAP_PORT`                     | `389`           | LDAP server port
`LDAP_SSL_VERIFY`               | `true`           | Validate certificate for `ldaps://` style URL
`LDAP_START_TLS`                | `false`         | Enable LDAP start TLS
`LDAP_USERNAME_CASE_SENSITIVE`  | `false`         | Kanboard lowercase the ldap username to avoid duplicate users (the database is case sensitive)
`LDAP_BIND_TYPE`                | `anonymous`     | Bind type: `anonymous`, `user` or `proxy`
`LDAP_USERNAME`                 | `null`          | LDAP username to use with proxy mode or username pattern to use with user mode
`LDAP_PASSWORD`                 | `null`          | LDAP password to use for proxy mode
`LDAP_USER_BASE_DN`             | Empty         | LDAP DN for users (Example: `CN=Users,DC=kanboard,DC=local`)
`LDAP_USER_FILTER`              | Empty         | LDAP pattern to use when searching for a user account (Example: `(&(objectClass=user)(sAMAccount Name=%s))`)
`LDAP_USER_ATTRIBUTE_USERNAME`  | `uid`           | LDAP attribute for username (Example: `samaccountname`)
`LDAP_USER_ATTRIBUTE_FULLNAME`  | `cn`            | LDAP attribute for user full name (Example: `displayname`)
`LDAP_USER_ATTRIBUTE_EMAIL`     | `mail`          | LDAP attribute for user email
`LDAP_USER_ATTRIBUTE_GROUPS`    | `memberof`      | LDAP attribute to find groups in user profile
`LDAP_USER_ATTRIBUTE_PHOTO`     | Empty         | LDAP attribute to find user photo (`jpegPhoto` or `thumbnailPhoto`)
`LDAP_USER_ATTRIBUTE_LANGUAGE`  | Empty         | LDAP attribute for user language (`preferredlanguage`), the accepted language format is `fr-FR`
`LDAP_USER_CREATION`            | `true`          | Enable automatic LDAP user creation
`LDAP_GROUP_ADMIN_DN`           | Empty         | LDAP DN for administrators (Example: `CN=Kanboard-Admins,CN=Users,DC=kanboard,DC=local`)
`LDAP_GROUP_MANAGER_DN`         | Empty         | LDAP DN for managers (Example: `CN=Kanboard Managers,CN=Users,DC=kanboard,DC =local`)
`LDAP_GROUP_PROVIDER`           | `false`         | Enable LDAP group provider for project permissions
`LDAP_GROUP_BASE_DN`            | Empty         | LDAP Base DN for groups
`LDAP_GROUP_FILTER`             | Empty         | LDAP group filter (Example: `(&(objectClass=group)(sAMAccoun tName=%s\*))`)
`LDAP_GROUP_USER_FILTER`        | Empty         | If defined, Kanboard will search user groups in `LDAP_GROUP_BASE_DN` with this filter, it's useful only for posixGroups (Example: `(&(objectClass=posixGroup)(mem berUid=%s))`)
`LDAP_GROUP_ATTRIBUTE_NAME`     | `cn`            | LDAP attribute for the group name
`LDAP_GROUP_USER_ATTRIBUTE`     | `username`      | LDAP attribute for the user in the group filter

LDAP Configuration Examples
---------------------------

### Microsoft Active Directory

- User authentication
- Download the user profile picture from Active Directory
- Set user language from LDAP attribute
- Kanboard roles are mapped to Active Directory groups
- LDAP group providers is enabled

```php
define('LDAP_AUTH', true);

define('LDAP_SERVER', 'my-ldap-server');
define('LDAP_PORT', 389);

define('LDAP_BIND_TYPE', 'proxy');
define('LDAP_USERNAME', 'administrator@kanboard.local');
define('LDAP_PASSWORD', 'secret');

define('LDAP_USER_BASE_DN', 'CN=Users,DC=kanboard,DC=local');
define('LDAP_USER_FILTER', '(&(objectClass=user)(sAMAccountName=%s))');

define('LDAP_USER_ATTRIBUTE_USERNAME', 'sAMAccountName');
define('LDAP_USER_ATTRIBUTE_FULLNAME', 'displayname');
define('LDAP_USER_ATTRIBUTE_PHOTO', 'jpegPhoto');
define('LDAP_USER_ATTRIBUTE_LANGUAGE', 'preferredLanguage');

define('LDAP_GROUP_ADMIN_DN', 'CN=Kanboard Admins,CN=Users,DC=kanboard,DC=local');
define('LDAP_GROUP_MANAGER_DN', 'CN=Kanboard Managers,CN=Users,DC=kanboard,DC=local');

define('LDAP_GROUP_PROVIDER', true);
define('LDAP_GROUP_BASE_DN', 'CN=Users,DC=kanboard,DC=local');
define('LDAP_GROUP_FILTER', '(&(objectClass=group)(sAMAccountName=%s*))');
define('LDAP_GROUP_ATTRIBUTE_NAME', 'cn');
```

### OpenLDAP with memberOf overlay

User LDIF example:

```
dn: uid=manager,ou=Users,dc=kanboard,dc=local
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
uid: manager
sn: Lastname
givenName: Firstname
cn: Kanboard Manager
displayName: Kanboard Manager
mail: manager@kanboard.local
userPassword: password
memberOf: cn=Kanboard Managers,ou=Groups,dc=kanboard,dc=local
```

Group LDIF example:

```
dn: cn=Kanboard Managers,ou=Groups,dc=kanboard,dc=local
objectClass: top
objectClass: groupOfNames
cn: Kanboard Managers
member: uid=manager,ou=Users,dc=kanboard,dc=local
```

Kanboard Configuration:

- User authentication
- Kanboard roles are mapped to LDAP groups
- LDAP group providers is enabled

```php
define('LDAP_AUTH', true);

define('LDAP_SERVER', 'my-ldap-server');
define('LDAP_PORT', 389);

define('LDAP_BIND_TYPE', 'proxy');
define('LDAP_USERNAME', 'cn=admin,DC=kanboard,DC=local');
define('LDAP_PASSWORD', 'password');

define('LDAP_USER_BASE_DN', 'OU=Users,DC=kanboard,DC=local');
define('LDAP_USER_FILTER', 'uid=%s');

define('LDAP_GROUP_ADMIN_DN', 'cn=Kanboard Admins,ou=Groups,dc=kanboard,dc=local');
define('LDAP_GROUP_MANAGER_DN', 'cn=Kanboard Managers,ou=Groups,dc=kanboard,dc=local');

define('LDAP_GROUP_PROVIDER', true);
define('LDAP_GROUP_BASE_DN', 'ou=Groups,dc=kanboard,dc=local');
define('LDAP_GROUP_FILTER', '(&(objectClass=groupOfNames)(cn=%s*))');
define('LDAP_GROUP_ATTRIBUTE_NAME', 'cn');
```

### OpenLDAP with Posix groups (memberUid)

User LDIF example:

```
dn: uid=manager,ou=Users,dc=kanboard,dc=local
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: manager
sn: Lastname
givenName: Firstname
cn: Kanboard Manager
displayName: Kanboard Manager
uidNumber: 10001
gidNumber: 8000
userPassword: password
homeDirectory: /home/manager
mail: manager@kanboard.local
```

Group LDIF example:

```
dn: cn=Kanboard Managers,ou=Groups,dc=kanboard,dc=local
objectClass: posixGroup
cn: Kanboard Managers
gidNumber: 5001
memberUid: manager
```

Kanboard Configuration:

- User authentication
- Kanboard roles are mapped to LDAP groups
- LDAP group providers is enabled

```php
define('LDAP_AUTH', true);

define('LDAP_SERVER', 'my-ldap-server');
define('LDAP_PORT', 389);

define('LDAP_BIND_TYPE', 'proxy');
define('LDAP_USERNAME', 'cn=admin,DC=kanboard,DC=local');
define('LDAP_PASSWORD', 'password');

define('LDAP_USER_BASE_DN', 'OU=Users,DC=kanboard,DC=local');
define('LDAP_USER_FILTER', 'uid=%s');

define('LDAP_GROUP_ADMIN_DN', 'cn=Kanboard Admins,ou=Groups,dc=kanboard,dc=local');
define('LDAP_GROUP_MANAGER_DN', 'cn=Kanboard Managers,ou=Groups,dc=kanboard,dc=local');

// This filter is used to find the groups of our user
define('LDAP_GROUP_USER_FILTER', '(&(objectClass=posixGroup)(memberUid=%s))');

define('LDAP_GROUP_PROVIDER', true);
define('LDAP_GROUP_BASE_DN', 'ou=Groups,dc=kanboard,dc=local');
define('LDAP_GROUP_FILTER', '(&(objectClass=posixGroup)(cn=%s*))');
define('LDAP_GROUP_ATTRIBUTE_NAME', 'cn');
```

### OpenLDAP with groupOfNames

User LDIF example:

```
dn: uid=manager,ou=Users,dc=kanboard,dc=local
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
uid: manager
sn: Lastname
givenName: Firstname
cn: Kanboard Manager
displayName: Kanboard Manager
mail: manager@kanboard.local
userPassword: password
```

Group LDIF example:

```
dn: cn=Kanboard Managers,ou=Groups,dc=kanboard,dc=local
objectClass: top
objectClass: groupOfNames
cn: Kanboard Managers
member: uid=manager,ou=Users,dc=kanboard,dc=local
```

Kanboard Configuration:

- User authentication
- Kanboard roles are mapped to LDAP groups
- LDAP group providers is enabled

```php
define('LDAP_AUTH', true);

define('LDAP_SERVER', 'my-ldap-server');
define('LDAP_PORT', 389);

define('LDAP_BIND_TYPE', 'proxy');
define('LDAP_USERNAME', 'cn=admin,DC=kanboard,DC=local');
define('LDAP_PASSWORD', 'password');

define('LDAP_USER_BASE_DN', 'OU=Users,DC=kanboard,DC=local');
define('LDAP_USER_FILTER', 'uid=%s');

define('LDAP_GROUP_ADMIN_DN', 'cn=Kanboard Admins,ou=Groups,dc=kanboard,dc=local');
define('LDAP_GROUP_MANAGER_DN', 'cn=Kanboard Managers,ou=Groups,dc=kanboard,dc=local');

// This filter is used to find the groups of our user
define('LDAP_GROUP_USER_FILTER', '(&(objectClass=groupOfNames)(member=uid=%s,ou=Users,dc=kanboard,dc=local))');

define('LDAP_GROUP_PROVIDER', true);
define('LDAP_GROUP_BASE_DN', 'ou=Groups,dc=kanboard,dc=local');
define('LDAP_GROUP_FILTER', '(&(objectClass=groupOfNames)(cn=%s*))');
define('LDAP_GROUP_ATTRIBUTE_NAME', 'cn');
```
