---
title: Users and Groups
toc: true
menu:
    main:
        parent: Using Kanboard
---

User Types
----------

In Kanboard, there are two types of users:

Type       | Description
-----------| ----------------------------------------------------------
Local User | User whose password is stored in Kanboard's database
Remote User| User credentials are managed by another system (e.g., LDAP server)

Examples of remote users:

- LDAP users
- Users authenticated by a reverse-proxy
- OAuth2 users

User Roles
----------

### Application Roles

Each Kanboard user has one of these roles:

Role                               | Description
-----------------------------------| -----------------------------------
Administrator                      | Access to everything
Manager                            | Can create team projects but cannot change application settings
User                               | Can create private projects only

### Project Roles

Each team project can assign a different role to each user and group:

Role            | Description
----------------|-----------------------------------------------------
Project Manager | Can change project settings, access the Gantt chart, and view reports
Project Member  | Can create tasks and use the board
Project Viewer  | Read-only access to the board and tasks

Custom project roles can be created to apply specific restrictions to users.

Groups Management
-----------------

In Kanboard, each user can be a member of one or more groups. A group is like a team or organization.

Only administrators can create new groups and assign users.

Groups can be managed from **User Management > View All Groups**. From there, you can create groups and assign users.

![Groups Management](/images/v1/groups-management.png)

Each project manager can authorize access to a set of groups from the project permissions page.

The external ID is mainly used for external group providers. Kanboard provides an LDAP group provider to automatically sync groups from LDAP servers.

Add a New User
--------------

To add a new user, you must be an administrator.

1. From the dropdown menu in the top-right corner, go to **User Management**.
2. At the top, click **New Local User** or **New Remote User**.
3. Fill out the form and save.

![New User](/images/v1/new-user.png)

When creating a **local user**, you must specify at least the following:

- **Username**: This is the unique identifier for the user (login).
- **Password**: The password must have at least 6 characters.

For **remote users**, only the username is mandatory.

Edit Users
----------

In the **Users** menu, you can see the list of users. To modify a user, click the **Edit** link.

- Regular users can only change their own profile.
- Administrators can edit any user.

Remove Users
------------

From the **Users** menu, click the **Remove** link. This link is visible only to administrators.

If you remove a user, **tasks assigned to them will be unassigned** after the operation.

Two-Factor Authentication
-------------------------

Each user can enable [two-factor authentication](http://en.wikipedia.org/wiki/Two_factor_authentication).
After a successful login, a one-time code (6 characters) is required to access Kanboard.

This code is provided by compatible software, usually installed on your smartphone or another device.

Kanboard uses the [Time-based One-time Password Algorithm](http://en.wikipedia.org/wiki/Time-based_One-time_Password_Algorithm) defined in [RFC 6238](http://tools.ietf.org/html/rfc6238).

Compatible software includes:

- [Google Authenticator](https://github.com/google/google-authenticator/) (Android, iOS, Blackberry)
- [FreeOTP](https://freeotp.github.io/) (Android, iOS)
- [OATH Toolkit](http://www.nongnu.org/oath-toolkit/) (Command-line utility on Unix/Linux)

This system can work offline, so you don't necessarily need a mobile phone.

### Configuration

1. Go to your user profile.
2. On the left, click **Two-Factor Authentication** and then click the button.
3. A secret key is generated for you.

![2fa](/images/v1/2fa.png)

- Save the secret key in your TOTP software. If you use a smartphone, the easiest solution is to scan the QR code with FreeOTP or Google Authenticator.
- Each time you open a new session, a new code will be required.
- Test your device before closing your session.

A new secret key is generated each time you enable/disable this feature.

{{< hint type="info" >}}
Since Kanboard v1.2.8, users with two-factor authentication enabled
must use API keys.
{{</ hint >}}
