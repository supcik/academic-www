+++
title = "Language and translation"

date = 2016-04-20
draft = false

toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.

math = false

[menu.docs]
    parent = "features"
    weight = 10
+++

Both the **interface** and **content** language can be changed to suit your needs.

## Interface

The **Interface Language** is used to change the language throughout your site. The following interface languages are currently available: English, 中文 (简体), Español, Português, Deutsch, Euskara, Français, Italiano, 日本語, 한국어, Nederlands, Polski, Русский, Türkçe, Tiếng Việt and Catalan.

The interface text is stored in language files which are collected from Academic's `themes/academic/i18n/` folder, as well as an `i18n/` folder at the root of your project.

To edit the interface text, copy `themes/academic/i18n/en.yaml` to `i18n/en.yaml` (relative to the root of your website). Open the new file and make any desired changes to the text appearing after `translation:`. Note that the language files are formatted in YAML syntax.

To translate the interface text to another language, follow the above instructions, but name the new file in the form `i18n/X.yaml` where `X` is the appropriate [ISO/RFC5646 language identifier](http://www.w3schools.com/tags/ref_language_codes.asp) for the translation. Then follow the brief instructions in the *Language* section at the bottom of your `config.toml`. To change the default language used by Academic, set `defaultContentLanguage` to the desired language identifier in your configuration file.

To translate the navigation bar, you can edit the default `[[main]]` instances in `config/_default/menu.toml`. However, for a multilingual site, you will need to duplicate this file to `config/_default/menu.XX.toml` and translate its menu items, where `XX` is the language identifier (e.g. `menu.zh.toml` for Simplified Chinese). Thus, the navigation bar can be displayed in multiple languages.

## Content

In this section, you will learn how to create content in multiple languages.

Move all you existing content in `content/` to a sub-folder named with the appropriate [ISO/RFC5646 language identifier](http://www.w3schools.com/tags/ref_language_codes.asp). For example, if your existing content is in English, move your content to `content/en/`.

To create content in an additional language, create a sub-folder in `content/` named with the appropriate [ISO/RFC5646 language identifier](http://www.w3schools.com/tags/ref_language_codes.asp). Then place your translated content in here, just as you would for your primary language content.

If a page has been translated into multiple languages, a language chooser will appear in the navigation bar to allow the user to select which language they would like to view the page in. 

You may also need to configure `config/_default/languages.toml` with the relevant content directories. This can be performed by creating a config section for each language and setting its `contentDir` to the relevant path. 

For further details on Hugo's internationalization and multilingual features, refer to the [associated Hugo documentation](https://gohugo.io/content/multilingual/).
