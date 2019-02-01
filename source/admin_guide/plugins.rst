Plugin Directory Configuration
==============================

To install, update and remove plugins from the user interface, you must
have those requirements:

-  The plugin directory must be writeable by the web server user
-  The Zip extension must be available on your server
-  The config parameter ``PLUGIN_INSTALLER`` must be set at ``true``

To enable this feature, change the value of ``PLUGIN_INSTALLER`` to
``true`` in your config file. You can also change the permissions of
the plugin folder on the filesystem.

Only administrators are allowed to install plugins from the user
interface.

By default, only plugin listed on Kanboard’s website are available.
You can change the directory URL in the config file.

.. warning:: Since Kanboard v1.2.8, the plugin directory is disabled by default
    for security reasons.

- There is no code review or any approval process to submit a plugin.
- This is up to the Kanboard instance owner to validate if a plugin is legit.
