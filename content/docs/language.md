+++
title = "Language and translation"

date = 2016-04-20
lastmod = 2018-01-20
draft = false

toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.

math = false

[menu.docs]
    parent = "setup"
    weight = 40
+++

Both the **interface** and **content** language can be changed to suit your needs.

## Interface

The **Interface Language** is used to change the language throughout your site. The following interface languages are currently available: English, 中文 (简体), Español, Português, Deutsch, Euskara, Français, Italiano, 日本語, 한국어, Nederlands, Polski, Русский, Türkçe, Tiếng Việt and Catalan.

The interface text is stored in language files which are collected from Academic's `themes/academic/i18n/` folder, as well as an `i18n/` folder at the root of your project.

To edit the interface text, copy `themes/academic/i18n/en.yaml` to `i18n/en.yaml` (relative to the root of your website). Open the new file and make any desired changes to the text appearing after `translation:`. Note that the language files are formatted in YAML syntax.

To translate the interface text to another language, follow the above instructions, but name the new file in the form `i18n/X.yaml` where `X` is the appropriate [ISO/RFC5646 language identifier](http://www.w3schools.com/tags/ref_language_codes.asp) for the translation. Then follow the brief instructions in the *Language* section at the bottom of your `config.toml`. To change the default language used by Academic, set `defaultContentLanguage` to the desired language identifier in your configuration file.

To translate the navigation bar, you can edit the default `[[menu.main]]` instances in `config.toml`. However, for a multilingual site, you will need to duplicate all of the `[[menu.main]]` instances and rename the new instances from `[[menu.main]]` to `[[Languages.X.menu.main]]`, where `X` is the language identifier (e.g. `[[Languages.zh.menu.main]]` for Simplified Chinese). Thus, the navigation bar can be displayed in multiple languages.

## Content

To translate a content file in your `content/` folder into another language, copy the file to `filename.X.md` where `filename` is your existing filename and `X` is the appropriate [ISO/RFC5646 language identifier](http://www.w3schools.com/tags/ref_language_codes.asp) for the translation. Then translate the content in the new file to the specified language.

If a page has been translated into multiple languages, a language chooser will appear in the navigation bar to allow the user to select which language they would like to view the page in. 

For further details on Hugo's internationalization and multilingual features, refer to the [associated Hugo documentation](https://gohugo.io/content/multilingual/).
