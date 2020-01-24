+++
title = "Language and translation"

date = 2016-04-20
draft = false

toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.
weight = 120

math = false

[menu.docs]
    parent = "features"
    weight = 10
+++

Both the **interface** and **content** language can be changed to suit your needs.

## Interface

The **Interface Language** is used to change the language throughout your site. By default, Academic activates the English language pack as the display language.

### Available Language Packs

Choose from **25+** interface languages including:

- **Català** (ca)
- **Dansk** (da)
- **Deutsch** (de)
- **Ελληνικά** (el)
- **English** (en)
- **Español** (es)
- **Eesti** (et)
- **Euskara** (eu)
- **Français** (fr)
- **Magyar** (hu)
- **Bahasa Indonesia** (id)
- **Italiano** (it)
- **日本語** (ja)
- **ភាសាខ្មែរ** (km)
- **한국어** (ko)
- **Latviešu** (lv)
- **Nederlands** (nl)
- **Polski** (pl)
- **Português** (pt)
- **Română** (ro)
- **Русский** (ru)
- **Svenska** (sv)
- **Türkçe** (tr)
- **Українська** (uk)
- **Tiếng Việt** (vi)
- **中文 (简体)** (zh)
- **中文 (繁體)** (zh-Hant)

### Setting the Language

Choose the languages you wish to use from the list above, noting their identifiers in brackets. Alternatively, a new language pack can be created by following the guide in the next section.

Follow the brief instructions in your `config/_default/languages.toml` to configure which language packs you wish to use.

To change the **default language** used by Academic, set `defaultContentLanguage` to the desired language identifier in your `config.toml` file.

### Create or Modify a Language Pack

The interface text is stored in language files which are collected from Academic's `themes/academic/i18n/` folder, as well as an `i18n/` folder at the root of your project.

To edit the interface text, copy a language pack such as `themes/academic/i18n/en.yaml` to your own `i18n` folder at the root of your site folder, so you have a path like `i18n/en.yaml`. Open the new file and make any desired changes to the text appearing after `translation:`. Note that the language files are formatted in YAML syntax.

To create a new language pack, translating the interface text to another language, follow the above instructions, but name the new file in the form `i18n/X.yaml` where `X` is the appropriate [ISO/RFC5646 language identifier](http://www.w3schools.com/tags/ref_language_codes.asp) for the translation.

If you translate the interface into a new language, please consider contributing it by opening a Pull Request on our GitHub.

### Navigation Bar

To translate the navigation bar, you can edit the default `[[main]]` instances in `config/_default/menu.toml`. However, for a multilingual site, you will need to duplicate this file to `config/_default/menu.XX.toml` and translate its menu items, where `XX` is the language identifier (e.g. `menu.zh.toml` for Simplified Chinese). Thus, the navigation bar can be displayed in multiple languages.

## Content

In this section, you will learn how to create content in multiple languages.

Move all you existing content in `content/` to a sub-folder named with the appropriate [ISO/RFC5646 language identifier](http://www.w3schools.com/tags/ref_language_codes.asp). For example, if your existing content is in English, move your content to `content/en/`.

To create content in an additional language, create a sub-folder in `content/` named with the appropriate [ISO/RFC5646 language identifier](http://www.w3schools.com/tags/ref_language_codes.asp). Then place your translated content in here, just as you would for your primary language content.

If a page has been translated into multiple languages, a language chooser will appear in the navigation bar to allow the user to select which language they would like to view the page in. 

You may also need to configure `config/_default/languages.toml` with the relevant content directories. This can be performed by creating a config section for each language and setting its `contentDir` to the relevant path. 

For further details on Hugo's internationalization and multilingual features, refer to the [associated Hugo documentation](https://gohugo.io/content/multilingual/).
