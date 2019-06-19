+++
title = "Customization"

date = 2016-04-20
toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.
weight = 110

math = true

[menu.docs]
    parent = "features"
    weight = 5
+++

It is possible to carry out many customizations *without* editing any code in the `themes/academic/` folder, making it easier to update the framework in the future.

## Custom theme

Both the **colour theme** and **font** can be customized.

To **customize the color theme**, you can copy a theme such as `themes/academic/data/themes/default.toml` to `data/themes/default.toml` (at the root of your site, **not** in `themes/academic/`), creating the `data/themes/` folders if they do not already exist. Now you can adjust the colors within your theme file using [HTML color codes](https://htmlcolorcodes.com).

To **customize the font theme**, you can copy a theme such as `themes/academic/data/fonts/default.toml` to `data/fonts/default.toml` (at the root of your site, **not** in `themes/academic/`), creating the `data/fonts/` folders if they do not already exist. Now you can adjust the font size and family, choosing from the library of [Google Fonts](https://fonts.google.com/) if you wish.

To select a free web-font available from Google Fonts:

1. Visit [Google Fonts](https://fonts.google.com)
2. Click `+` on the fonts you wish to use
3. Open the `Families Selected` dialog box at the bottom
4. Under **Embed Font**, copy the part of the URL in bold and paste it as the `google_fonts` option in your new font theme
    - For example, if Google gives you `<link href="https://fonts.googleapis.com/css?family=B612+Mono|Open+Sans&display=swap" rel="stylesheet">`, set `google_fonts = "B612+Mono|Open+Sans"`
5. Under **Specify in CSS** in Google Font's dialog, copy the font name and paste it as one of the fonts in your font theme
    - For example, given `font-family: 'B612 Mono', monospace;`, copy `B612 Mono`

### Naming your theme

If you rename a theme file, the associated `color_theme` or `font_theme` values in `config/_default/params.toml` will also need to be updated to reflect the new name. Avoid using spaces in filenames.

### Example

An example of a custom theme in action can be found in the [repo for this site](https://github.com/sourcethemes/academic-www/blob/master/data/themes/academic.toml) - refer to `data/themes/academic.toml` and the value of `theme` in `params.toml`,

### Share your theme

If you create your own theme, consider giving it a unique name and *sharing* your new color or font theme with the [community](http://discuss.gohugo.io/).

## Website icon

Save your main icon and mobile icon as square PNG images named `icon.png` (32x32 pixels) and `icon-192.png` (192x192 pixels), respectively. Place them in your root `static/img/` folder.

## Analytics

To enable [Google Analytics](http://www.google.com/analytics), add your tracking code in `config/_default/config.toml` similarly to `googleAnalytics = "UA-12345678-9"`.

To integrate other third party analytics services, refer to the **Add Scripts** section.

## Comments

The Disqus commenting variable (`disqusShortname`) in `config/_default/config.toml` can be set to your own [Disqus](https://disqus.com/) shortname to enable visitors to comment on your posts.

## Add scripts (JS)

To add a **third party script**, create a file named `custom_js.html` in a `layouts/partials/` folder at the root of your website (not in the `themes` folder). Any HTML code added to this file will be included within your website's footer.

Whereas for your own **local scripts**, let's say that you have a JS file named `custom.js`. We can place your file in  `assets/js/` (create the folders within your website root if they don't exist). Then open your `config/_default/params.toml` and set `plugins_js = ["custom"]`, where *custom* is your JS filename without its extension.

## Page Sharer

The *Page Sharer* enables you to **grow your audience** by engaging your visitors to share pages on your site with others. Visitors can share your pages via **email, Twitter, Facebook, LinkedIn, WhatsApp, Weibo, and many more!**

To enable the Page Sharer, set `sharing` to `true` in your `config/_default/params.toml`. Alternatively, it can be enabled or disabled on a per page basis using `share` in your page front matter.

To customize the Page Sharer, edit `data/page_sharer.toml`. If you don't already have this file in your site, update to Academic **v4.4+** (if necessary) and copy the `themes/academic/data/page_sharer.toml` file to `data/page_sharer.toml`.

### Select your social networks

To enable or disable a button, set its `enable` option to `true` or `false`.

### Reorder your social networks

To reorder buttons, move the `[[buttons]]` instances to your preferred order.

### Add a new social network

We've already included some of the most popular networks, but further networks can easily be added. To add a button for a new social network, duplicate a `[[buttons]]` instance and edit its properties. [Choose an icon]({{< relref "page-builder.md#icons" >}}), and give it a `title` and a one-word, lowercase `id`. Once you have the sharing URL for the new social network, paste it into the `url` field, substituting the title of the page to share with `{title}` and page URL with `{url}`.

## Custom head

To add custom **metadata** or scripts to your website's `<head>`, create a file named `custom_head.html` in a `layouts/partials/` folder at the root of your website (not in the `themes` folder) and add your HTML code.

This approach can also be used for adding third party scripts with an *async* or *defer* attribute to the site head.

**NOTE: Prior to v4.4.0-dev, `head_custom.html` is used rather than `custom_head.html`.**

## Permalinks

*Permalinks*, or *permanent links*, are URLs to individual pages and posts on your website. They are permanent web addresses which can be used to link to your content. Using Hugo's *permalinks* option these can be easily customized. For example, the blog post URL can be changed to the form *yourURL/2016/05/01/my-post-slug* by adding the following near the end of your `config/_default/config.toml`:

    [permalinks]
        post = "/:year/:month/:day/:slug"

Where `:slug` defaults to the filename of the post, excluding the file extension. However, slug may be overridden on a per post basis if desired, simply by setting `slug = "my-short-post-title"` in your post preamble.

**Example 2:** let's consider changing the URL path of posts from `post/` to `blog/`. First, add the following parameters to your `config/_default/config.toml`:
```
[permalinks]
    post = "/blog/:slug"
```
Then add `aliases = ["/blog/"]` to your post archive page at `post/_index.md` so that it can be accessed from the */blog/* URL.

## Customize style (CSS)

To personalize Academic, you can **choose a colour theme and font theme** in `config/_default/params.toml`.

For further personalization, you can [**create your own colour theme and font theme**](#custom-theme).

If advanced style customization is required, **CSS code** can be written to override or enhance the existing styles.

Given some custom CSS named `custom.css`, we can place it in `assets/css/` (create the folders within your website root if they don't exist). Then open your `config/_default/params.toml` and set `plugins_css = ["custom"]`, where *custom* is your CSS filename without its extension.

## Override a template

Hugo uses a [template lookup](https://gohugo.io/templates/lookup-order/) which enables you to override any of Academic's files without directly changing them. This can make it easier to update Academic in the future since you do not modify any of Academic's files directly.

To override a template in the theme, you simply copy the file you are interested in from `themes/academic/` and paste it in your site folder using a similar path. To understand how this works, you should familiarize yourself with template lookup. Finally, when you update Academic, remember to compare your version of the file against Academic's one, in case you need to propagate any changes across.

For example, say we wish to add some HTML code to the navigation bar. Let's copy the relevant file `themes/academic/layouts/partials/navbar.html` to `layouts/partials/navbar.html` (at the root of your site, **not** in `themes/academic/`), creating the `layouts/partials/` folders if they do not already exist. Now you can add the HTML code you want to your copy of the file, which will override Academic's version.

## Date Format

Academic uses the following constants to format dates and times:

| Type     | Options |
|----------|--------------------------------------------------------------------------------------------------|
| Year     | `06`   `2006` |
| Month    | `01`   `1`   `Jan`   `January` |
| Day      | `02`   `2`   `_2` <span style="font-size:90%;">(width two, right justified)</span> |
| Weekday  | `Mon`   `Monday` |
| Hours    | `03`   `3`   `15` |
| Minutes  | `04`   `4` |
| Seconds  | `05`   `5` |
| AM/PM    | `PM`   `pm` |
| Timezone | `MST` |
| Offset   | `-0700`   `-07`   `-07:00`   `Z0700`   `Z07:00` |

To modify the format, edit `date_format` and `time_format` in `config/_default/params.toml` using the above constants. For example, some common formats are:

| Format                            | Type              |
|-----------------------------------|-------------------|
| `January 2, 2006`                 | Date              |
| `01/02/06`                        |                   |
| `Jan-02-06`                       |                   |
| `Mon, 02 Jan 2006`                |                   |
| `Monday, 02 Jan 2006`             |                   |
| `15:04`                           | Time              |
| `3:04 PM`                         |                   |
| `15:04 MST`                       |                   |
