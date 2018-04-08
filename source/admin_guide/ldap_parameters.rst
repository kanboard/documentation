LDAP Configuration Parameters
=============================

Here is the list of available LDAP parameters:

+-----------------------+----------+----------------------------------+
| Parameter             | Default  | Description                      |
|                       | value    |                                  |
+=======================+==========+==================================+
| ``LDAP_AUTH``         | false    | Enable LDAP authentication       |
+-----------------------+----------+----------------------------------+
| ``LDAP_SERVER``       | Empty    | LDAP server hostname             |
+-----------------------+----------+----------------------------------+
| ``LDAP_PORT``         | 389      | LDAP server port                 |
+-----------------------+----------+----------------------------------+
| ``LDAP_SSL_VERIFY``   | true     | Validate certificate for         |
|                       |          | ``ldaps://`` style URL           |
+-----------------------+----------+----------------------------------+
| ``LDAP_START_TLS``    | false    | Enable LDAP start TLS            |
+-----------------------+----------+----------------------------------+
| ``LDAP_USERNAME_CASE_ | false    | Kanboard lowercase the ldap      |
| SENSITIVE``           |          | username to avoid duplicate      |
|                       |          | users (the database is case      |
|                       |          | sensitive)                       |
+-----------------------+----------+----------------------------------+
| ``LDAP_BIND_TYPE``    | anonymou | Bind type: “anonymous”, “user”   |
|                       | s        | or “proxy”                       |
+-----------------------+----------+----------------------------------+
| ``LDAP_USERNAME``     | null     | LDAP username to use with proxy  |
|                       |          | mode or username pattern to use  |
|                       |          | with user mode                   |
+-----------------------+----------+----------------------------------+
| ``LDAP_PASSWORD``     | null     | LDAP password to use for proxy   |
|                       |          | mode                             |
+-----------------------+----------+----------------------------------+
| ``LDAP_USER_BASE_DN`` | Empty    | LDAP DN for users (Example:      |
|                       |          | “CN=Users,DC=kanboard,DC=local”) |
+-----------------------+----------+----------------------------------+
| ``LDAP_USER_FILTER``  | Empty    | LDAP pattern to use when         |
|                       |          | searching for a user account     |
|                       |          | (Example:                        |
|                       |          | “(&(objectClass=user)(sAMAccount |
|                       |          | Name=%s))”)                      |
+-----------------------+----------+----------------------------------+
| ``LDAP_USER_ATTRIBUTE | uid      | LDAP attribute for username      |
| _USERNAME``           |          | (Example: “samaccountname”)      |
+-----------------------+----------+----------------------------------+
| ``LDAP_USER_ATTRIBUTE | cn       | LDAP attribute for user full     |
| _FULLNAME``           |          | name (Example: “displayname”)    |
+-----------------------+----------+----------------------------------+
| ``LDAP_USER_ATTRIBUTE | mail     | LDAP attribute for user email    |
| _EMAIL``              |          |                                  |
+-----------------------+----------+----------------------------------+
| ``LDAP_USER_ATTRIBUTE | memberof | LDAP attribute to find groups in |
| _GROUPS``             |          | user profile                     |
+-----------------------+----------+----------------------------------+
| ``LDAP_USER_ATTRIBUTE | Empty    | LDAP attribute to find user      |
| _PHOTO``              |          | photo (jpegPhoto or              |
|                       |          | thumbnailPhoto                   |
+-----------------------+----------+----------------------------------+
| ``LDAP_USER_ATTRIBUTE | Empty    | LDAP attribute for user language |
| _LANGUAGE``           |          | (preferredlanguage), the         |
|                       |          | accepted language format is      |
|                       |          | “fr-FR”                          |
+-----------------------+----------+----------------------------------+
| ``LDAP_USER_CREATION``| true     | Enable automatic LDAP user       |
|                       |          | creation                         |
+-----------------------+----------+----------------------------------+
|``LDAP_GROUP_ADMIN_DN``| Empty    | LDAP DN for administrators       |
|                       |          | (Example:                        |
|                       |          | “CN=Kanboard-Admins,CN=Users,DC= |
|                       |          | kanboard,DC=local”)              |
+-----------------------+----------+----------------------------------+
| ``LDAP_GROUP_MANAGER_ | Empty    | LDAP DN for managers (Example:   |
| DN``                  |          | “CN=Kanboard                     |
|                       |          | Managers,CN=Users,DC=kanboard,DC |
|                       |          | =local”)                         |
+-----------------------+----------+----------------------------------+
|``LDAP_GROUP_PROVIDER``| false    | Enable LDAP group provider for   |
|                       |          | project permissions              |
+-----------------------+----------+----------------------------------+
| ``LDAP_GROUP_BASE_DN``| Empty    | LDAP Base DN for groups          |
|                       |          |                                  |
+-----------------------+----------+----------------------------------+
| ``LDAP_GROUP_FILTER`` | Empty    | LDAP group filter (Example:      |
|                       |          | “(&(objectClass=group)(sAMAccoun |
|                       |          | tName=%s*))“)                    |
+-----------------------+----------+----------------------------------+
| ``LDAP_GROUP_USER_FIL | Empty    | If defined, Kanboard will search |
| TER``                 |          | user groups in                   |
|                       |          | LDAP_GROUP_BASE_DN with this     |
|                       |          | filter, it’s useful only for     |
|                       |          | posixGroups (Example:            |
|                       |          | ``(&(objectClass=posixGroup)(mem |
|                       |          | berUid=%s))``)                   |
+-----------------------+----------+----------------------------------+
| ``LDAP_GROUP_ATTRIBUT | cn       | LDAP attribute for the group     |
| E_NAME``              |          | name                             |
+-----------------------+----------+----------------------------------+

.. note::  LDAP attributes must be in lowercase
