+++
title = "Getting Started With the Page Builder"
date = 2016-04-19
aliases = ["/docs/widgets/"]

toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.

linktitle = "Build your homepage"
[menu.docs]
  parent = "setup"
  weight = 35
+++

**Building beautiful pages is easy with Academic's widget system. No programming is required!**

Loading pre-made layouts is a great way to *kickstart* your new homepage. [Academic Kickstart]({{< relref "install.md" >}}) comes with some popular **Sections** preconfigured for this purpose. A **Widget** can be added inside each Section. Hence, you can have multiple instances of widgets, such as listing recent pages of different content types or categories.

Widgets empower you to fully customize your site. They display as sections on the homepage or on [widget pages]({{< relref "managing-content.md" >}}). They can be added, removed, and positioned as desired.

Academic comes with the following widgets built-in. Additionally, third-party widgets can also be [developed](#develop-a-new-widget) and installed.

- [Blank](#blank) - add [any elements]({{< relref "writing-markdown-latex.md" >}}) such as an image gallery
- [Hero](#hero) - encourage visitors to perform an action (CTA)
- [About](#about) - introduce yourself
- [Featurette](#featurette) - showcase skills or key features of a product
- [Accomplishments](#accomplishments) - showcase your (online learning) certificates and other achievements
- [Pages](#pages) - display recent blog posts, talks, and publications
- Featured - display featured (i.e. *sticky*) blog posts, talks, and publications
- [Contact](#contact) - display your contact details, including an optional contact form and map
- Portfolio - a filterable portfolio
- Tag cloud - enable visitors to discover popular topics
- People - introduce your team members
- Slider (carousel) - promote a lot of content in a small space

## Using Widgets

Academic Kickstart includes instances of all the built-in widgets. Delete the sections in `content/home/` that you don't need (or set `active = false` in their front matter) and personalize the front matter options of the sections that you wish to keep by opening them in a text editor.

The sections (widget instances) in your `home/` folder can be renamed to anything you like (but use hyphens instead of spaces). Just remember to update your main menu in `config/_default/menus.toml` if you have a link to the widget instance.

### Add a widget to the homepage

To add a widget manually, copy the relevant widget from `themes/academic/exampleSite/content/home/` to your `content/home/` folder. 

Widget identifiers are set to their respective filenames, so a `content/home/about.md` widget can be linked from the navigation bar by setting the relevant URL as `"#about"` in `config/_default/menu.toml`.

This means that if you want to use multiple instances of a widget, each widget will be assigned a unique ID based on the filename that you set. You can then use that ID for linking, like in the above example.

### Remove a widget from the homepage

If you do not require a particular widget, you can simply delete any associated files from the `content/home/` folder.

To remove a navigation link from the top of the page, remove the associated `[[main]]` entry in `config/_default/menu.toml`.

### Position sections

The order that the homepage widgets are displayed in is defined by the `weight` parameter in each of the files in the `content/home/` directory. The widgets are displayed in ascending order of their `weight`, so you can simply edit the `weight` parameters as desired.

### Develop a new widget

This section guides developers to create custom widgets using HTML and CSS. You may also be interested in the [Blank widget]({{< relref "page-builder.md#blank" >}}).

Let's create a new widget, the *Awesome* widget. First create the `layouts/partials/widgets/` folder structure in the root of your site (**not in** `themes/academic/`).

Next, create the widget file `awesome.html` in your new `layouts/partials/widgets/` folder.

Now we can open `awesome.html` in a text editor and create our desired layout using HTML and [Hugo's Go Templating](https://gohugo.io/templates/introduction/). Styling can be performed by [adding new CSS styles via the Custom CSS feature]({{< relref "customization.md#customize-style-css" >}}). In this example, let's add the following code to our `awesome.html` widget which will display the section content in a large blue font:

```html
<div style="font-size: 2rem; color: blue">
  {{ .page.Content }}
</div>
```

Finally, we will instantiate the widget on the website by creating a Markdown file, `my-widget.md` in `content/home/` and adding the following front matter to the file:

```toml
+++
widget = "awesome"  # Do not modify this line!
active = true  # Activate this widget? true/false
weight = 1  # Order that this section will appear in.
+++

Everything is awesome!
```

Good luck creating your own widgets and feel free to [share them with the community](http://discuss.gohugo.io). You can also  [open a PR on Github](https://github.com/gcushen/hugo-academic/pulls) for your widget to be considered for integration as a core Academic widget. For inspiration, you can [check out how the in-built widgets were made](https://github.com/gcushen/hugo-academic/tree/master/layouts/partials/widgets).

## Personalizing Widgets

The parameters for each section consist of general options in addition to widget-specific options. When you open a section installed in the `content/home/` folder in a text editor, the available options will be displayed in the front matter (between the pair of `+++`).

Generally, if you write any text in the file body after a widget's front matter, your text will appear at the top of the widget. This can be useful for introducing the widget content.

A title and subtitle can be set for most widgets using the `title` and `subtitle` options respectively.

### Columns

The number of columns in a section can be configured for the **Blank** and **Portfolio** widgets. Valid options are:

- `"1"`: a single full-width column with the section content appearing directly underneath the section title (if set)
- `"2"`: two columns in the classic Academic layout with the the section title appearing on the left and the section content appearing on the right

For example:

```toml
[design]
  # Choose how many columns the section has. Valid values: 1 or 2.
  columns = "1"
```

### View

Several widgets have a `view` option to let you choose the layout of the widget. The following layouts are available: 

- 1 = List (previously Simple)
- 2 = Compact (previously Stream)
- 3 = Card (previously Detailed)
- 4 = Citation (previously APA and MLA), only available for publications
  - Optionally, edit the value of `citation_style` in `params.toml` to APA or MLA
- 5 = Showcase (large images), only available for projects

### Icons

Academic enables you to use a wide range of icons from [Font Awesome](https://fontawesome.com/icons?d=gallery) and [Academicons](https://jpswalsh.github.io/academicons/).

Icon pack "fab" includes the following **brand** icons:

- twitter, weixin, weibo, linkedin, github, facebook, pinterest, twitch, youtube, instagram, soundcloud
- [See all icons](https://fontawesome.com/icons?d=gallery&s=brands)

Icon packs "fas" and "far" include the following **general** icons:

- fax, envelope (for email), comments (for discussion forum)
- [See all icons](https://fontawesome.com/icons?d=gallery&s=regular,solid)

Icon pack "ai" includes the following **academic** icons:

- cv, google-scholar, arxiv, orcid, researchgate, mendeley
- [See all icons](https://jpswalsh.github.io/academicons/)

### Background

A background can easily be applied to any homepage section. Choose from a range of background options including **color, gradient, and image**. Then choose either a dark or light text color, by setting `text_color_light`.

Once you have chosen the type of background, delete or comment out (by prefixing `#`) any unused options. For example, if you choose an image background, set the `image*` and `text_color_light` options and delete the rest (delete `color` and `gradient*`). For colors, any [HTML color name](https://html-color-codes.info/color-names/) or [Hex value](https://html-color-codes.info) is valid.

The following excerpt shows the front matter structure for defining a background:

```toml
[background]
  # Background color.
  color = "navy"
  
  # Background gradient.
  gradient_start = "#4bb4e3"
  gradient_end = "#2b94c3"
  
  # Background image.
  image = "background.jpg"  # Name of image in `static/img/`.
  image_darken = 0.6  # Darken the image? Range 0-1 where 0 is transparent and 1 is opaque.

  # Text color (true=light or false=dark).
  text_color_light = true
```

### Style

It's possible to customize the style of a specific instance of a widget. For example, the background of a widget may be changed to an image or color gradient.

First, define your custom style in CSS using the [CSS Plugin]({{< relref "customization.md#customize-style-css" >}}) feature.

To apply your new style to a widget, set `css_class` in a widget's front matter. For example `css_class = "MY_CSS_CLASS"`, where `MY_CSS_CLASS` is the name of the CSS class which you defined in the previous step.

Custom CSS code can also be directly applied to a section using the `css_style` option.

```toml
[advanced]
 # Custom CSS. 
 css_style = ""
 
 # CSS class.
 css_class = ""
```

## Blank

You can use the Blank widget to create your own home page sections.

Simply duplicate (copy/paste) and rename the example *Demo* file at `content/home/demo.md`. Then edit the section title, weight (refer to *Position Sections*), and content as desired. You may write your widget content in Markdown, shortcodes, or even HTML.

You may also wish to add a navigation link to the top of the page that points to the new section. This can be achieved by adding something similar to the following lines to your `content/_default/menu.toml`, where the URL will consist of the first title word in lowercase:

    [[main]]
        name = "Research"
        url = "#research"
        weight = 10

You may also be interested in the [developing widgets](#develop-a-new-widget).

## Hero

The Hero widget can be used to encourage visitors to perform an action (CTA). It's the first thing that visitors see when they visit your website, and it influences the way your visitors feel and behave on your site.

Typically, the Hero widget is configured to include a hero image, a tagline and a call to action (CTA). There are other possibilities as well though, such as including a secondary action, note, and [background](#background).

{{< figure library="1" src="docs/widget-hero.png" title="The Hero widget can be used to encourage visitors to perform an action (CTA)." >}}

Edit the front matter of `home/hero.md` to add the primary action that you would like your visitors to perform.

For example, the following options can be added to your section front matter in order to include the Hero widget: 

```toml
widget = "hero"

# ... Put Your Section Options Here (title etc.) ...

# Hero image (optional). Enter filename of an image in the `static/img/` folder.
hero_media = ""

# Call to action links (optional).
#   Display link(s) by specifying a URL and label below. Icon is optional for `[cta]`.
#   Remove a link/note by deleting a cta/note block.
[cta]
  url = "https://sourcethemes.com/academic/docs/install"
  label = "Get Started"
  icon_pack = "fas"
  icon = "download"
  
[cta_alt]
  url = "https://sourcethemes.com/academic/"
  label = "View Documentation"

# Note. An optional note to show underneath the links.
[cta_note]
  label = ""
```

In this example, we have [associated an icon](#icons) with the action (`[cta]` option).

## Featurette

As an individual, use the Featurette widget to showcase your skills and expertise. As an organization, use the widget to highlight the key features of your product or service.

{{< figure library="1" src="docs/widget-featurette.png" title="Showcase personal skills or product features with the Featurette widget." >}}

Edit the front matter of `home/skills.md` to add your skills/features. [Choose from a large range of icons to depict the skills/features](#icons).

For example, the following options can be added to your section front matter in order to include the Featurette widget: 

```toml
widget = "featurette"

# ... Put Your Section Options Here (title etc.) ...

# Showcase personal skills or business features.
# Add/remove as many `[[feature]]` blocks below as you like.
# For available icons, see: https://sourcethemes.com/academic/docs/widgets/#icons
[[feature]]
  icon = "r-project"
  icon_pack = "fab"
  name = "R"
  description = "90%"
  
[[feature]]
  icon = "chart-line"
  icon_pack = "fas"
  name = "Statistics"
  description = "100%"  
  
[[feature]]
  icon = "camera-retro"
  icon_pack = "fas"
  name = "Photography"
  description = "10%"
```

## Contact

The contact widget will automatically display the following information according to what you entered in `config/_default/params.toml`:

- [contact form](#contact-form) or an email link (see section below)
- [contact links](#contact-links) such as for Twitter, Skype, Weixin, Weibo, Discussion Forums, etc.
- phone number
- address
- office hours
- appointment booking link
- map

For example, the following options can be added to your section front matter in order to include the Contact widget: 

```toml
widget = "contact"

# ... Put Your Section Options Here (title etc.) ...

# Automatically link email and phone?
autolink = true

# Email form provider
#   0: Disable email form
#   1: Netlify (requires that the site is hosted by Netlify)
#   2: formspree.io
email_form = 2
```

### Contact links

Academic enables you to use a wide range of icons in your contact links. [Learn more about icons](#icons).

### Contact form

You can choose whether to display simply an email address or a contact form. This can be chosen in `content/home/contact.md` by setting the `email_form` option. If set to 0, it will display your email address as a link, based on the value of `email` that you entered in `config/_default/params.toml`. If set to 1, it will use [Netlify](https://www.netlify.com/docs/form-handling/) to add a contact form with a captcha test so that visitors can send you email and spam from bots is prevented.

{{% alert note %}}
The Netlify option is only available if you are hosting your site with Netlify. In this case, user messages to you will be sent to your Netlify account admin panel. A webhook can be created in your Netlify account if you wish to forward messages to your email address. When using Netlify to provide the contact form, you do not need to provide a value for `email` in `config/_default/params.toml` since the messages will be delivered to your Netlify admin panel.
{{% /alert %}}

Otherwise, if set to 3, the widget will display a contact form using the `email` in `config/_default/params.toml` and will use the [Formspree](https://formspree.io) service for sending the email to you. For this method, simply send yourself a test message after you have configured the contact form. Formspree will then send you an email to verify your new account with them. Note that **Formspree is usually blocked for Chinese visitors** as it uses Google reCAPTCHA (unless you upgrade to Formspree's paid plan in order to disable reCAPTCHA).

## About

Introduce yourself to your readers.

{{< figure library="1" src="docs/widget-about.png" title="Introduce yourself to your readers with the About widget." >}}

[Setup a user profile]({{< relref "get-started.md" >}}) and then edit the front matter of `home/about.md` to associate the About widget with your username (name of the folder your created in `authors/`).

For example, the following options can be added to your section front matter in order to include the About widget: 

```toml
widget = "about"

# ... Put Your Section Options Here (title etc.) ...

# Choose the user profile to display
# This should be the username of a profile in your `content/author/` folder.
author = "admin"
```

## Accomplishments

List your accomplishments including certificates and courses attended.

{{< figure library="1" src="docs/widget-accomplishments.png" title="List your accomplishments including certificates and courses attended." >}}

Add your accomplishments by editing the front matter of `home/accomplishments.md`. For example:

```toml
widget = "accomplishments"

# ... Put Your Section Options Here (title etc.) ...

# Date format
#   Refer to https://sourcethemes.com/academic/docs/customization/#date-format
date_format = "Jan 2006"

# Accomplishments.
#   Add/remove as many `[[item]]` blocks below as you like.
#   `title`, `organization` and `date_start` are the required parameters.
#   Leave other parameters empty if not required.
#   Begin/end multi-line descriptions with 3 quotes `"""`.

[[item]]
  organization = "Coursera"
  organization_url = "https://www.coursera.org"
  title = "Neural Networks and Deep Learning"
  url = ""
  certificate_url = "https://www.coursera.org"
  date_start = "2018-10-01"
  date_end = ""
  description = ""

[[item]]
  organization = "edX"
  organization_url = "https://www.edx.org"
  title = "Blockchain Fundamentals"
  url = "https://www.edx.org/professional-certificate/uc-berkeleyx-blockchain-fundamentals"
  certificate_url = "https://www.edx.org"
  date_start = "2018-03-01"
  date_end = ""
  description = "Formulated informed blockchain models, hypotheses, and use cases."
  
[[item]]
  organization = "DataCamp"
  organization_url = "https://www.datacamp.com"
  title = "Object-Oriented Programming in R: S3 and R6 Course"
  url = ""
  certificate_url = "https://www.datacamp.com"
  date_start = "2017-07-01"
  date_end = "2017-12-21"
  description = ""
```

## Pages

List your recently published pages such as blog posts, talks, and publications.

{{< figure library="1" src="docs/widget-publications.png" title="List your recent pages." >}}

There are three sections in the demo that use the *Pages* widget. These include `home/posts.md`, `home/talks.md`, and `home/publications.md`.

Edit the front matter of a section to personalize the [view](#view) and other options shown below:

```toml
widget = "pages"  # Use the Pages widget

# ... Put Your Section Options Here (title etc.) ...

[content]
  # Page type to display. E.g. post, talk, or publication.
  page_type = "post"
  
  # Choose how much pages you would like to display (0 = all pages)
  count = 5
  
  # Choose how many pages you would like to offset by
  offset = 0

  # Page order. Descending (desc) or ascending (asc) date.
  order = "desc"

  # Filter posts by a taxonomy term.
  [content.filters]
    tag = ""
    category = ""
    publication_type = ""
    exclude_featured = false
    exclude_past = false
    exclude_future = false
    
[design]
  # Toggle between the various page layout types.
  #   1 = List
  #   2 = Compact
  #   3 = Card
  #   4 = Citation (publication only)
  view = 2
```
