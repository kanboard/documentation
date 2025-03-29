---
title: Building JavaScript and CSS Files
menu:
    main:
        parent: Contributing to Kanboard
aliases:
    - /en/latest/developer_guide/assets.html
---

Stylesheet and JavaScript files are merged and minified.

- Original CSS files are stored in `assets/css/src/*.css`.
- Original JavaScript files are stored in `assets/js/src/*.js`.

## Requirements

- PHP
- Local checkout of the Git repository

## Instructions

### Build JavaScript

```bash
./cli js
```

### Build Stylesheets

```bash
./cli css
```

{{< hint type="info" >}}
Building assets is not possible from Kanboard's archive. You must clone the repository.
{{</ hint >}}
