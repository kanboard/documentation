---
title: Autentificación Two-Factor
menu:
    main:
        parent: Guía del usuario
---

Cada usuario puede habilitar la [autenticación de dos factores](http://en.wikipedia.org/wiki/Two_factor_authentication).
Después de un inicio de sesión exitoso, un código de un solo uso (6 caracteres) se le pide al usuario para permitir el acceso a Kanboard.

Este código tiene que ser proporcionado por un software compatible generalmente instalado en tu smartphone.

Kanboard usa el [Time-based One-time Password Algorithm](http://en.wikipedia.org/wiki/Time-based_One-time_Password_Algorithm) definido en el [RFC 6238](http://tools.ietf.org/html/rfc6238).

Existen muchos softwares compatibles con el estándar del sistema TOTP.
Por ejemplo, puedes usar estas aplicaciones libres y de código abierto:

- [Google Authenticator](https://github.com/google/google-authenticator/) (Android, iOS, Blackberry)
- [FreeOTP](https://freeotp.github.io/) (Android, iOS)
- [OATH Toolkit](http://www.nongnu.org/oath-toolkit/) (Utilidad en línea de comandos Unix/Linux)

Este sistema puede trabajar offline y no es necesario tener un teléfono móvil.

Instalación
-----------

1. Ir a tu perfil de usuario
2. Click a la izquierda en **Two factor authentication** y seleccionar la caja
3. Una clave secreta es generada para ti

![2FA](/images/v1/2fa.png)

- Tienes que guardar la clave secreta en tu software TOTP. Si usas un smartphone, la solución será más fácil ya que puedes escanear el QR code con FreeOTP o Google Authenticator.
- Cada vez que abras una nueva sesión, un nuevo código se pedirá.
- No olvides verificar el dispositivo antes de cerrar la sesión.

Una nueva clave secreta es generada cada vez que actives o desactives esta función.