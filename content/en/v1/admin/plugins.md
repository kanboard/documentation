---
title: Plugins Installation
toc: true
aliases:
    - /en/latest/admin_guide/plugins.html
    - /en/1.2.24/admin_guide/plugins.html
    - /en/1.2.23/admin_guide/plugins.html
    - /en/1.2.22/admin_guide/plugins.html
    - /en/1.2.21/admin_guide/plugins.html
    - /en/1.2.20/admin_guide/plugins.html
    - /en/1.2.19/admin_guide/plugins.html
---

{{< hint type="warning" >}}
Since Kanboard v1.2.8, installing plugins from the web interface is disabled by default for security reasons.
{{</ hint >}}

To install, update and remove plugins from the user interface, you must have these requirements:

- The plugin directory must be writeable by the web server user.
- The PHP Zip extension must be available on your server.
- The config parameter `PLUGIN_INSTALLER` must be set to `true`.

Only administrators are allowed to install plugins from the user interface.

By default, only plugins listed on Kanboard's website are available.
You can change the directory URL by using the config option `PLUGIN_API_URL`.

If you are using the Docker image, you can refers to the [Kanboard Docker documentation for examples of configuration]({{< relref "docker.md" >}}).

{{< hint type="info" >}}
- There is no code review or any approval process to submit a plugin.
- This is up to the Kanboard instance owner to validate if a plugin is legit.
{{</ hint >}}
