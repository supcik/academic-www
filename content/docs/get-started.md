+++
title = "Getting started"

date = 2016-04-20
#lastmod = 2018-01-20
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

## Choose the right theme for you

Check out the [available color themes]({{< relref "../themes.md" >}}) and have fun choosing a design you love.

Once you have settled on a theme, edit your `config.toml` file in a text editor and set the `color_theme` option to the name of the chosen theme.

The following font styles are also available and can be set by the `font` option in `config.toml`:

- default (modern)
- classic (original Academic v1 style)
- playfair (traditional serif)

Don't worry if you are not 100% happy with the colors or font yet, as these can be fully customized later on.

## Choose the right layout for you

Academic has a template for you whether you are you creating a website for your CV, academic research, blog, course, lab, business, photography, portfolio, or restaurant!

What kind of content would you like to publish? Academic supports:

- **Pages**: any general content
- **Widget Pages**: pages that can consist of numerous widgets, such as the **homepage**
- **Posts**: blog posts or news
- **Projects**: publish your portfolio or projects
- **Online Courses**: share knowledge online
- **Software Documentation**: document your software projects
- **Talks**: publish any talks which you are presenting
- **Slides**: write slides very efficiently with Markdown, present them at your talk, and share them online
- **Publications**: import your research publications from BibTeX

Once you have decided on the type of content that you would like to publish, take a look at the [available homepage widgets]({{< relref "widgets.md" >}}) and consider which ones would be most relevant to you.

Then, open your `content/home/` folder and set the `active` parameter to either `true` or `false` for each widget depending on if you wish to display it or not. Widgets that you don't need can alternatively be deleted rather than setting `active` to `false`.

Next, let's **order the widgets** according to your preference. To move a widget up or down, increase or decrease the value of the `weight` parameter in each widget which you activated. The widgets will be ordered in ascending order of these weights and there is no need for the weights to be consecutive numbers.

{{% alert note %}}
If your `content/home/` folder is empty, populate it from the [example]({{< relref "install.md#demo-content" >}}).
{{% /alert %}}

## Customize it

After selecting a theme and a layout, make it your own.

### Core parameters

The core parameters for the website can be edited in the `config.toml` configuration file:

- Set `baseurl` to your website URL (this will be provided by your host such as [Netlify]({{< relref "deployment.md" >}}))
  - Come back to this option later if you are unsure
- Set `title` to your desired website title, such as your name
- Edit your personal/business details under `[params]`; these will be displayed mainly in the homepage *about* and *contact* widgets (if used). To disable a contact field, simply clear the value to `""`. 
- Place a square cropped portrait photo named `portrait.jpg` into the `static/img/` folder, overwriting any defaults. Note that you can edit the `avatar` filepath to point to a different image name or clear the value to disable the avatar feature. Alternatively, set `gravatar` to `true` to use the Gravatar/Wordpress avatar associated with your `email` address.
- If you write mathematical content, set `math = true`, otherwise leave it as `false`
- Social/academic networking links are defined as multiples of `[[params.social]]`. They can be created or deleted as necessary.

### Menu

The `[[menu.main]]` entries towards the bottom of `config.toml` define the navigation links at the top of the website. They can be added or removed as desired, based on the layout which you chose above.

To link to a section of the homepage, use the form `#<section-filename>` where `<section-filename>` is the filename (without .md extension). For example, `#posts` references a section with filename `posts.md`. You can rename your section files in `content/home/`, just remember to use a dash (`-`) instead of spaces in the filename. 

{{% alert note %}}
To create a dropdown sub-menu, add `identifier = "something"` to the parent item and `parent = "something"` to the child item.
{{% /alert %}}

### Introduce yourself

Edit your biography in the *about* widget `content/home/about.md` that you copied across from the `themes/academic/exampleSite/` folder. The research interests and qualifications are stored as `interests` and `education` variables. The academic qualifications are defined as multiples of `[[education.courses]]` and can be created or deleted as necessary. It's possible to completely hide the interests and education lists by deleting their respective variables.

### Add your content

Refer to our guide on [managing content]({{< relref "managing-content.md" >}}) to create your own content such as blog posts, publications, talks, and projects.

### Remove any unused example pages

[Delete any unused example pages]({{< relref "managing-content.md#removing-content" >}}).

{{% alert note %}}
You will likely want to keep the `_index.md` files (notice the underscore prefix) as they configure your archive page for each content type (e.g. an index of all your blog posts).
{{% /alert %}}

## View your site

If you installed on your computer with **Git** or **ZIP**, view your new website by running the `hugo server` command.

If you installed using **RStudio**, run `blogdown::serve_site()` to preview your site in your web browser. We recommend previewing your site in your normal web browser as the in-built RStudio web browser is very outdated and buggy.

Now visit [localhost:1313](http://localhost:1313) and your new Academic powered website will appear. Otherwise, if using **Netlify**, they will provide you with your URL.

## Deploy your site

Publish your site to the world by following the [deployment steps]({{< relref "deployment.md" >}}).
