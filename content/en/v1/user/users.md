---
title: Users and Groups
toc: true
menu:
    main:
        parent: Using Kanboard
---

User Types
----------

In Kanboard there are two types of users:

Type       | Description
-----------| ----------------------------------------------------------
Local User | User that stores his password in Kanboard's database
Remote User| User credentials are managed by another system (Example: LDAP server)

Examples of remote users:

- LDAP user
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

Each individual team project can assign a different role to each user and group:

Role            | Description
----------------|-----------------------------------------------------
Project Manager | Can change project settings, access to the Gantt chart and reports
Project Member  | Can create tasks and use the board
Project Viewer  | Read-only access to the board and tasks

Custom project roles can be created to apply a set of restrictions to the users.

Groups Management
-----------------

In Kanboard, each user can be a member of one or many groups. A group is like a team or an organization.

Only administrators can create new groups and assign users.

Groups can be managed from **User management > View All Groups**. From there, you can create groups and assign users.

![Groups Management](/images/v1/groups-management.png)

Each project manager can authorize the access to a set of groups from the project permissions page.

The external id is mainly used for external group providers. 
Kanboard provides an LDAP group provider to automatically sync groups from LDAP servers.

Add a New User
--------------

To add a new user, you must be an administrator.

1. From the dropdown menu in the top right corner, go to the menu **Users Management**
2. On the top, you have a link **New local user** or **New remote user**
3. Fill the form and save

![New User](/images/v1/new-user.png)

When you create a **local user**, you have to specify at least those values:

- **username**: This is the unique identifier of your user (login)
- **password**: The password of your user must have at least 6 characters

For **remote users**, only the username is mandatory.

Edit Users
----------

When you go to the **users** menu, you have the list of users, to modify a user click on the **edit link**.

- If you are a regular user, you can change only your own profile
- You have to be an administrator to be able to edit any users

Remove Users
------------

From the **users** menu, click on the link **remove**. 
This link is visible only if you are an administrator.

If you remove a specific user, **tasks assigned to this person will be unassigned** after the operation.

Two-Factor Authentication
-------------------------

Each user can enable the [two-factor authentication](http://en.wikipedia.org/wiki/Two_factor_authentication).
After a successful login, a one-time code (6 characters) is asked to the user to allow access to Kanboard.

This code has to be provided by a compatible software usually installed on your smartphone or a different device.

Kanboard use the [Time-based One-time Password Algorithm](http://en.wikipedia.org/wiki/Time-based_One-time_Password_Algorithm) defined in the [RFC 6238](http://tools.ietf.org/html/rfc6238).

There are many software compatible with the standard TOTP system. For example, you can use these applications:

- [Google Authenticator](https://github.com/google/google-authenticator/) (Android, iOS, Blackberry)
- [FreeOTP](https://freeotp.github.io/) (Android, iOS)
- [OATH Toolkit](http://www.nongnu.org/oath-toolkit/) (Command line utility on Unix/Linux)

This system can work offline and you don't necessarily need to have a mobile phone.

### Configuration

1. Go to your user profile
2. On the left, click on **Two Factor Authentication** and click on the button
3.  A secret key is generated for you

![2fa](/images/v1/2fa.png)

- You have to save the secret key in your TOTP software. If you use a smartphone, the easiest solution is to scan the QR code with FreeOTP or Google Authenticator.
- Each time you will open a new session, a new code will be asked
- Don't forget to test your device before closing your session

A new secret key is generated each time you enable/disable this feature.

{{< hint type="info" >}}
Since Kanboard v1.2.8, people with two-factor authentication enabled
must use API keys.
{{</ hint >}}
