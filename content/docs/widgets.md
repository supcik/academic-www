+++
title = "Widgets"

date = 2016-04-19
# lastmod = 2018-01-20
draft = false

aliases = ["widgets/"]

toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.

[menu.docs]
  parent = "setup"
  weight = 35
+++

Widgets empower you to fully customize your site. They display as sections on the homepage or on [widget pages]({{< relref "managing-content.md" >}}). They can be enabled or disabled and configured as desired.

Academic comes with the following widgets built-in. Additionally, third-party widgets can also be [developed](#develop-a-new-widget) and installed.

- [Custom widget](#custom) - add your own content!
- [Featurette](#featurette) - showcase skills or key features of a product
- [Accomplishments](#accomplishments) - showcase your (online learning) certificates and other achievements
- Recent news/blog posts
- [Contact](#contact)
- [About](#about) - introduce yourself
- Projects
- Featured publications
- [Recent publications](#publications) - for academics, researchers, and publishers
- Featured talks
- Recent talks
- Tag cloud
- Hero (call-to-action)
- Carousel

Academic Kickstart includes instances of all the built-in widgets. Delete the widgets in `content/home/` that you don't need (or set `active = false` in their front matter) and personalize the front matter options of the widgets you wish to keep by opening them in a text editor.

The parameters for each widget vary. They can be found in the front matter (between the pair of `+++`) for each widget installed in the `content/home/` folder.

Generally, if you write any text in the file body after a widget's front matter, your text will appear at the top of the widget. This can be useful for introducing the widget content.

The widget instances in your `home/` folder can be renamed to anything you like (but use hyphens instead of spaces). Just remember to update your main menu in `config/_default/menus.toml` if you have a link to the widget instance.

## Using Widgets

### Add a widget to the homepage

To add a widget manually, copy the relevant widget from `themes/academic/exampleSite/content/home/` to your `content/home/` folder. 

Widget identifiers are set to their respective filenames, so a `content/home/about.md` widget can be linked from the navigation bar by setting the relevant URL as `"#about"` in `config.toml`.

This means that if you want to use multiple instances of a widget, each widget will be assigned a unique ID based on the filename that you set. You can then use that ID for linking, like in the above example.

### Remove a widget from the homepage

If you do not require a particular widget, you can simply delete any associated files from the `content/home/` folder.

To remove a navigation link from the top of the page, remove the associated `[[menu.main]]` entry in `config.toml`.

### Position widgets

The order that the homepage widgets are displayed in is defined by the `weight` parameter in each of the files in the `content/home/` directory. The widgets are displayed in ascending order of their `weight`, so you can simply edit the `weight` parameters as desired.

### Develop a new widget

This section guides developers to create custom widgets using HTML and CSS. You may also be interested in the [custom widget]({{< relref "widgets.md#custom" >}}).

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

## Custom

You can use the custom widget to create your own home page sections.

Simply duplicate (copy/paste) and rename the example *teaching* file at `content/home/teaching.md`. Then edit the section title, weight (refer to *Ordering sections* below), and content as desired. You may write your widget content in Markdown, shortcodes, or even HTML.

You may also wish to add a navigation link to the top of the page that points to the new section. This can be achieved by adding something similar to the following lines to your `config.toml`, where the URL will consist of the first title word in lowercase:

    [[menu.main]]
        name = "Research"
        url = "#research"
        weight = 10

You may also be interested in the [developing widgets](#develop-a-new-widget).

## Featurette

As an individual, use the Featurette widget to showcase your skills and expertise. As an organization, use the widget to highlight the key features of your product or service.

{{< figure library="1" src="docs/widget-featurette.png" title="Showcase personal skills or product features with the Featurette widget." >}}

Edit the front matter of `home/skills.md` to add your skills/features.

## Contact

The contact widget will automatically display the following information according to what you entered in `config/_default/params.toml`:

- [contact form](#contact-form) or an email link (see section below)
- [contact links](#contact-links) such as for Twitter, Skype, Weixin, Weibo, Discussion Forums, etc.
- phone number
- address
- office hours
- appointment booking link
- map

### Contact links

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

## Accomplishments

List your accomplishments including certificates and courses attended.

{{< figure library="1" src="docs/widget-accomplishments.png" title="List your accomplishments including certificates and courses attended." >}}

Add your accomplishments by editing the front matter of `home/accomplishments.md`.

## Publications

List your recent or featured publications.

{{< figure library="1" src="docs/widget-publications.png" title="List your recent or featured publications." >}}

Edit the front matter of `home/publications.md` to personalize the layout. Choose from the following layouts:

- Simple
- Detailed
- APA citation style
- MLA citation style
- Stream (as pictured in the above screenshot)
