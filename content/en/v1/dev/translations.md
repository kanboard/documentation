---
title: Translations
toc: true
menu:
    main:
        parent: Contributing to Kanboard
---

## How to Translate Kanboard to a New Language

- Translations are stored in the directory `app/Locale`.
- Each language has its own subdirectory, e.g., French is `fr_FR`, Italian is `it_IT`, etc.
- A translation is a PHP file that returns an `Array` with key-value pairs.
- The key is the original English text, and the value is the translation in the corresponding language.
- **French translations are always up to date.**
- Always use the latest version (`main` branch).

### Create a New Translation

1. Create a new directory: `app/Locale/xx_XX` (e.g., `app/Locale/fr_CA` for French Canadian).
2. Create a new file for the translation: `app/Locale/xx_XX/translations.php`.
3. Use the content of the French locales and replace the values.
4. Update the file `app/Model/Language.php`.
5. Test with your local Kanboard installation.
6. Submit a [pull request on GitHub](https://help.github.com/articles/using-pull-requests/).

### Update an Existing Translation

1. Open the translation file `app/Locale/xx_XX/translations.php`.
2. Missing translations are commented with `//` and have empty values. Fill in the blanks and remove the comments.
3. Test with your local Kanboard installation.
4. Submit a [pull request](https://help.github.com/articles/using-pull-requests/).

## Adding New Translated Text in the Application

Translations are displayed using the following functions in the source code:

- `t()`: Displays text with HTML escaping.
- `e()`: Displays text without HTML escaping.

Always use the English version in the source code.

Text strings use the `sprintf()` function to replace elements:

- `%s` replaces a string.
- `%d` replaces an integer.

Refer to the [PHP documentation](http://php.net/sprintf) for all available formats.

## Finding Missing Translations in the Application

Run the following command in a terminal:

```bash
./cli locale:compare
```

This displays all missing and unused translations. Add missing translations to the French locale and sync other locales (see below).

## Synchronizing Translation Files

Run this command in your terminal:

```bash
./cli locale:sync
```

The French translation is used as the reference for other locales.
