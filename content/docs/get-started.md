+++
title = "Getting started"

date = 2016-04-20
lastmod = 2018-01-20
draft = false

toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.

math = true

aliases = ["post/getting-started/"]

[menu.docs]
    parent = "setup"
    weight = 20
+++

This quick tutorial will show you how to setup and use Academic.

## Core parameters

The core parameters for the website can be edited in the `config.toml` configuration file:

- Set `baseurl` to your website URL (we recommend [GitHub Pages](https://georgecushen.com/create-your-website-with-hugo/) for free hosting)
- Set `title` to your desired website title such as your name
- The example Disqus commenting variable should be cleared (e.g. `disqusShortname = ""`) or set to your own [Disqus](https://disqus.com/) shortname to enable commenting
- Edit your details under `[params]`; these will be displayed mainly in the homepage *about* and *contact* widgets (if used). To disable a contact field, simply clear the value to `""`. 
- Place a square cropped portrait photo named `portrait.jpg` into the `static/img/` folder, overwriting any defaults. Note that you can edit the `avatar` filepath to point to a different image name or clear the value to disable the avatar feature. Alternatively, set `gravatar` to `true` to use the Gravatar/Wordpress avatar associated with your `email` address.
- To enable LaTeX math for your site, set `math = true`
- Social/academic networking links are defined as multiples of `[[params.social]]`. They can be created or deleted as necessary.

## Introduce yourself

Edit your biography in the *about* widget `content/home/about.md` that you copied across from the `themes/academic/exampleSite/` folder. The research interests and qualifications are stored as `interests` and `education` variables. The academic qualifications are defined as multiples of `[[education.courses]]` and can be created or deleted as necessary. It's possible to completely hide the interests and education lists by deleting their respective variables.

## Customize the homepage

Refer to our guide on using [widgets]({{< relref "../widgets.md" >}}) to customize your homepage.

## Add your content

Refer to our guide on [managing content]({{< relref "managing-content.md" >}}) to create your own publications, blog posts, talks, and projects.

## Remove unused widgets and pages

[How to remove unused widgets and content pages]({{< relref "managing-content.md#removing-content" >}}).

## Themes

Check out the [available color themes]({{< relref "../themes.md" >}}) and set the theme using  the `color_theme` option in `config.toml`.

The following font styles are available and can be set by the `font` option in `config.toml`:

- default (modern)
- classic (original Academic v1 style)
- playfair (serif)

To **customize the color theme**, you can copy a theme such as `themes/academic/data/themes/default.toml` to `data/themes/default.toml` (at the root of your site, **not** in `themes/academic/`), creating the `data/themes/` folders if they do not already exist. Now you can adjust the colors within your theme file. Consider renaming and *sharing* your new color theme with the [community](http://discuss.gohugo.io/).

To **customize the font theme**, you can copy a theme such as `themes/academic/data/fonts/default.toml` to `data/fonts/default.toml` (at the root of your site, **not** in `themes/academic/`), creating the `data/fonts/` folders if they do not already exist. Now you can adjust the font size and family. Consider renaming and *sharing* your new font theme with the [community](http://discuss.gohugo.io/).

## View your site

If you installed on your computer with **Git** or **ZIP**, view your new website by running the `hugo server` command.

If you installed using **RStudio**, run `blogdown::serve_site()` to preview your site in your web browser. We recommend previewing your site in your normal web browser as the in-built RStudio web browser is very outdated and buggy.

Now visit [localhost:1313](http://localhost:1313) and your new Academic powered website will appear. Otherwise, if using **Netlify**, they will provide you with your URL.
