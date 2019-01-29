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

Widgets empower you to fully customize your site. They display as sections on the homepage or on widget pages. They can be enabled/disabled and configured as desired. Academic has the following widgets available to use:

- [Custom widget]({{< relref "widgets.md#custom" >}}) (add your own content!)
- Featurette (showcase key features or skills)
- Recent news/blog posts
- [Contact]({{< relref "widgets.md#contact" >}})
- About/biography
- Projects
- Featured publications
- Recent publications
- Featured talks
- Recent talks
- Tag cloud
- Hero (call-to-action)
- Carousel

The example site that you copied to create your site uses all the different types of widget (except talks), so you can generally just delete the widgets you don't need and customize the parameters of the widgets you wish to keep.

The parameters for each widget vary. They can be found in the preamble/frontmatter (between the pair of `+++`) for each widget installed in the `content/home/` folder.

Generally, if you write any text after the widget front matter, your text will appear at the top of the widget. This can be useful for introducing the widget content.

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

## Contact

The contact widget will automatically display the following information according to what you entered in `config.toml`:

- contact form or an email link (see section below)
- phone number
- address
- office hours
- appointment booking link
- map
- Skype
- Telegram
- Keybase

### Contact form

You can choose whether to display simply an email address or a contact form. This can be chosen in `content/home/contact.md` by setting the `email_form` option. If set to 0, it will display your email address as a link, based on the value of `email` that you entered in `config.toml`. If set to 1, it will use [Netlify](https://www.netlify.com/docs/form-handling/) to add a contact form with a captcha test so that visitors can send you email and spam from bots is prevented.

{{% alert note %}}
The Netlify option is only available if you are hosting your site with Netlify. In this case, user messages to you will be sent to your Netlify account admin panel. A webhook can be created in your Netlify account if you wish to forward messages to your email address. When using Netlify to provide the contact form, you do not need to provide a value for `email` in `config.toml` since the messages will be delivered to your Netlify admin panel.
{{% /alert %}}

Otherwise, if set to 3, the widget will display a contact form using the `email` in `config.toml` and will use the [Formspree](https://formspree.io) service for sending the email to you. For this method, simply send yourself a test message after you have configured the contact form. Formspree will then send you an email to verify your new account with them. Note that Formspree is usually blocked for Chinese visitors as it uses Google reCAPTCHA (unless you upgrade to Formspree's paid plan in order to disable reCAPTCHA).

### Publications

{{% alert note %}}
By default, publications will be displayed in a simple list. If you prefer a more detailed list with abstract and image, you can enable the detailed publication list on the homepage by changing the `list_format` in `content/home/publications.md`.
{{% /alert %}}
