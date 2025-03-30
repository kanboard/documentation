---
title: Authentication Providers
toc: true
menu:
    main:
        parent: Developing Plugins
---

New authentication backends can be written with very few lines of code.

Provider Registration
---------------------

In the method `initialize()` of your plugin, call the method `register()` of the class `AuthenticationManager`:

```php
public function initialize()
{
    $this->authenticationManager->register(new ReverseProxyLdapAuth($this->container));
}
```

The object provided to the method `register()` must implement one of the pre-defined authentication interfaces.

These interfaces are defined in the namespace `Kanboard\Core\Security`:

- `Kanboard\Core\Security\PreAuthenticationProviderInterface`
- `Kanboard\Core\Security\PostAuthenticationProviderInterface`
- `Kanboard\Core\Security\PasswordAuthenticationProviderInterface`
- `Kanboard\Core\Security\OAuthAuthenticationProviderInterface`

The only requirement is to implement the interfaces. Your class can be written in any way you prefer and located anywhere on the disk.

User Provider
-------------

When authentication is successful, your driver must return an object that represents the user. This object must implement the interface `Kanboard\Core\User\UserProviderInterface`.

Examples of authentication plugins
-----------------------------------

- [Authentication providers included in Kanboard](https://github.com/kanboard/kanboard/tree/master/app/Auth)
- [Reverse-Proxy Authentication with LDAP support](https://github.com/kanboard/plugin-reverse-proxy-ldap)
- [SMS Two-Factor Authentication](https://github.com/kanboard/plugin-sms-2fa)
