---
title: Building Javascript and CSS files
menu:
    main:
        parent: Contributing to Kanboard
aliases:
    - /en/latest/developer_guide/assets.html
---

Stylesheet and Javascript files are merged together and minified.

- Original CSS files are stored in the folder `assets/css/src/*.css`
- Original Javascript code is stored in the folder `assets/js/src/*.js`

Requirements
------------

- PHP
- Local checkout of the Git repository

Instructions
------------

Build Javascript:

```bash
./cli js
```

Build stylesheets:

```bash
./cli css
```

{{< hint type="info" >}}
Building assets is not possible from the Kanboard's archive, you have to clone the repository.
{{</ hint >}}
