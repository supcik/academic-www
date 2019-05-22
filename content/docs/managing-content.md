+++
date = 2016-04-18
title = "Managing content"
aliases = ["post/managing-content/"]

toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.
weight = 60

[menu.docs]
  parent = "content"
  weight = 20
+++

This is a brief guide to managing content with the Academic framework. Content can include news/blog posts, publications, projects, talks, widget pages, and much more. After you have read this guide about creating and managing content, you may also be interested to learn about [writing content with Markdown, LaTeX, and Shortcodes]({{< relref "writing-markdown-latex.md" >}}).<!--more-->

{{% alert warning %}}
Most front matter snippets in the documentation have recently been converted **[from TOML to YAML]({{< relref "front-matter.md" >}})**. The example widgets and configuration files remain in TOML format. Academic and Hugo continue to support both formats. An [online YAML<-->TOML converter is available](https://toolkit.site/format.html) should you need it. This change is to facilitate editing content in popular Markdown editors like [Typora](https://www.typora.io) and [Visual Studio Code](https://code.visualstudio.com).
{{% /alert %}}

## Introduction

The following common metadata can be added to the [front matter]({{< relref "front-matter.md" >}}) of most types of page in Academic.

**Core metadata:**

- **title**: the title of your page
- **summary**: a one-sentence summary of the content on your page. The summary can be shown on the homepage and can also benefit your search engine ranking.
- **date**: the [RFC 3339 date](https://github.com/toml-lang/toml#local-date-time) that the page was published. A future date will schedule the page to be published in the future. If you use the `hugo new ...` commands described on this page, the date will be filled automatically when you create a page. Also see **lastmod** and **publishDate**.
- **authors**: display the authors of the page and link to their user profiles if they exist. To link to a user profile, [create a user]({{< relref "/docs/get-started.md#introduce-yourself" >}}) based on the [*admin* template](https://github.com/gcushen/hugo-academic/tree/master/exampleSite/content/authors) and reference their username (the name of a user in your `authors` folder) in the `authors` field, e.g. `authors: ["admin"]`.
- **tags**: tagging your content helps users to discover similar content on your site. Tags can improve search relevancy and are displayed after the page content and also in the [Tag Cloud widget]({{< relref "page-builder.md" >}}). E.g. `tags: ["Electronics", "Diodes"]`.

**Popular metadata:**

- **subtitle**: an optional subtitle that will be displayed under the title
- **featured**: by setting `featured: true`, a page can be displayed in the [Featured widget]({{< relref "page-builder.md" >}}). This is useful for *sticky, announcement blog posts* or *selected publications* etc.
- **categories**: categorizing your content helps users to discover similar content on your site. Categories can improve search relevancy and display at the top of a page alongside a page's metadata. E.g. `categories: ["Art"]`.
- **lastmod**: the [RFC 3339 date](https://github.com/toml-lang/toml#local-date-time) that the page was last modified. If using Git, enable `enableGitInfo` in `config.toml` to have the page modification date automatically updated, rather than manually specifying `lastmod`.
- **publishDate**: the [RFC 3339 date](https://github.com/toml-lang/toml#local-date-time) that the page was published. You only need to specify this option if you wish to set **date** in the future but publish the page *now*, as is the case for publishing a journal article that is to appear in a journal etc.
- **draft**: by setting `draft: true`, only you will see your page when you preview your site  locally on your computer

A complete list of standard options can be found on the corresponding [Hugo docs page](https://gohugo.io/content-management/front-matter/#predefined).

### Featured image

To display a **featured image** in content pages, simply drag an image named `featured.*` (e.g. `featured.jpg`) into your page's folder.

{{% alert note %}}
If your page does not have its own folder ([*page bundle*](https://gohugo.io/content-management/page-bundles/)) within its section folder, you can refactor a page named `NAME.md` to `NAME/index.md`, creating the folder `NAME`. There is a [tool to help automate this process](https://github.com/sourcethemes/academic-scripts). Page bundles require Academic v3+ and Hugo v0.50+.
{{% /alert %}}

Want to caption the image or set a focal point to influence how the image is cropped? The parameters below can be added to the bottom of your page front matter to customize the appearance of the image. The caption supports Markdown and can be used to write an image caption or credit. The focal point ensures that automatic resizes of the image keep the subject in view.

```yaml
# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
image:
  # Caption (optional)
  caption: "Photo by [Academic](https://sourcethemes.com/academic/)"
  # Focal point (optional)
  # Options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
  focal_point: "Center"
  # Show image only in page previews?
  preview_only: false
```

### Page resources

Buttons can be generated in the page header to link to associated resources.

The example below shows how to create a Twitter link for a project and how to create a link to a post that was originally published on Medium:

```yaml
links:
  - icon_pack: fab
    icon: twitter
    name: Follow
    url: 'https://twitter.com/Twitter'
  - icon_pack: fab
    icon: medium
    name: Originally published on Medium
    url: 'https://medium.com'

```

The only required option is `url`, giving you the option to show a *text button*, an *icon button*, or a *combination of both*. [Learn more about icons]({{< relref "page-builder.md#icons" >}}). 

{{% alert warning %}}
Prior to 13th February 2019, `links` was known as `url_custom`.
{{% /alert %}}

To generate a **PDF button**, add a PDF file with the same name as your page's own folder to your page's folder and a PDF link will be automatically generated. For example, if your page is located at `publication/photons/index.md`, place a PDF at `publication/photons/photons.pdf`. This can be useful for talks and publications.

There are also several special built-in buttons that can be setup using `url_...` options in the front matter of some content types.

### Page features

The following parameters can be added to the front matter of a page (such as a blog post) to control its features:

```yaml
reading_time: false  # Show estimated reading time?
share: false  # Show social sharing links?
profile: false  # Show author profile?
comments: false  # Show comments?
```

### Math and Code

To enable **LaTeX math** rendering for a page, you should include `math: true` in the page's [front matter]({{< relref "front-matter.md" >}}), as demonstrated in the included example site. Otherwise, to enable math on the homepage or for all pages, you must globally set `math = true` in `params.toml`.

To disable **source code highlighting** for all pages, set `highlight = false` in `params.toml`. You can then enable source code highlighting only on pages that need it by setting `highlight: true` in that page's [front matter]({{< relref "front-matter.md" >}}). See the [code highlighting guide]({{< relref "writing-markdown-latex.md#code-highlighting" >}}) for further details.

### Header image

To display a full width **header image**, the header parameters below can be inserted towards the end of a page's [front matter]({{< relref "front-matter.md" >}}). It is assumed that the image is located in your `static/img/` media library, so the full path in the example below will be `static/img/header.png`. The `caption` parameter supports Markdown and can be used to write an image caption or credit. This option can be particularly useful for adding to an archive page's `_index.md` (e.g. to display at `YOUR_URL/post/` for the blog post archive).

```yaml
header:
  image: "header.png"
  caption: "Image credit: [**Academic**](https://github.com/gcushen/hugo-academic/)"
```

## Create a page

Pages are the most fundamental building block for content. They're useful for general standalone content which does not match one of the built-in content types on this page. You may also be interested in [Widget Pages](#create-a-widget-page) which enable you to add widgets to a page.

The simplest way of adding a page is to add a Markdown file using a `.md` extension at the root folder of your site.

For a site with just a homepage and an author, here's what the root directory and associated URLs might look like with a new page named *example*:

```plaintext
.
|-- authors/    # => https://example.com/authors/
|-- example/index.md    # => https://example.com/example/
└── home/  # => https://example.com/
```

And here's some example content for `example/index.md`:

```yaml
---
title: An example title
summary: Here we describe how to add a page to your site.
date: "2018-06-28T00:00:00Z"

reading_time: false  # Show estimated reading time?
share: false  # Show social sharing links?
profile: false  # Show author profile?
comments: false  # Show comments?

# Optional header image (relative to `static/img/` folder).
header:
  caption: ""
  image: ""
---

Add your *content* here...

```

If you have a lot of pages, you can organize them within a folder, for example:

 ```plaintext
.
|-- authors/    # => https://example.com/authors/
|-- example/about.md    # => https://example.com/example/about/
|-- example/terms.md    # => https://example.com/example/terms/
└── home/  # => https://example.com/
```

### Linking to your new page

To link to your new page from the site navigation bar, edit `config/_default/menu.toml`. Add a new menu entry similar to:

```toml
[[main]]
  name = "My new page"  # A link title for your page.
  url = "example/"  # The URL of your page.
  weight = 50  # The position of your page in the menu.
```

To link to your new page from another page, add something like `[My CV]{{</* ref "cv/index.md" */>}}` to the content of one of your existing pages.

### Example: creating a Curriculum Vitae page

Create a `cv/index.md` page for your Curriculum Vitae in your `content` folder. Add a front matter to the file, similar to that above, and add the content of your Curriculum Vitae below the front matter. Then create a link to your new page by following the steps in the above section.

Alternatively, for the above example, we could use a PDF of your Curriculum Vitae. For this purpose, create a folder called `files` within your `static` folder and move a PDF file named `cv.pdf` to that location, so we have a `static/files/cv.pdf` file path. The PDF can then be linked to from any content by using the code: `{{%/* staticref "files/cv.pdf" */%}}Download my CV{{%/* /staticref */%}}`.

## Create a widget page

So you would like to create a page which utilizes Academic's widget system, similar to the homepage?

{{% alert note %}}
To manage the home page (a special Widget Page), refer to the [Getting Started]({{< relref "get-started.md#choose-the-right-layout-for-you" >}}) and [Page Builder]({{< relref "page-builder.md" >}}) guides.
{{% /alert %}}

Create a new folder in your `content` folder, naming it with your new page name. In this example, we will create a *landing* page by creating a `content/landing/` folder to contain our new sections (widget instances).

Within your new `content/landing/` folder, create a file named `index.md` containing the following YAML parameters:

```yaml
---
title: "Landing Page"  # Add a page title.
summary: "Hello!"  # Add a page description.
date: "2019-01-01T00:00:00Z"  # Add today's date.
type: "widget_page"  # Page type is a Widget Page
---
```

Now, we can [**use the page builder to add sections**]({{< relref "page-builder.md" >}}) into your `content/landing/` folder. Widgets can also be copied from your `content/home/` folder or the `themes/academic/exampleSite/content/home/` demo site folder.

We can also [create a menu link]({{< relref "get-started.md#menu" >}}) to our new Widget Page. Given a Widget Page folder named `landing`, open `config/_default/menu.toml` in your editor and add:

```toml
[[main]]
  name = "My Widget Page"  # Title of the link.
  url = "landing/"  # Widget Page folder name.
  weight = 2  # Position of the link in the navigation bar.
```

{{% alert warning %}}
To create the new widget pages, an Academic version from **18 March 2019** onwards is required (corresponding to *v4.2 dev* or greater).
{{% /alert %}}

## Create a blog post

To create a blog/news article:

    hugo new  --kind post post/my-article-name

Then edit the newly created file `content/post/my-article-name.md` with your full title and content.

Hugo will automatically generate summaries of posts that appear on the homepage. If you are dissatisfied with an automated summary, you can either limit the summary length by appropriately placing <code>&#60;&#33;&#45;&#45;more&#45;&#45;&#62;</code> in the article body, or completely override the automated summary by adding a `summary` parameter to the `+++` preamble such that:

    summary: "Summary of my post."

To disable commenting for a specific post, you can add `disable_comments: true` to the post `+++` preamble. Or to disable commenting for all posts, you can either set `disqusShortname = ""` in `config.toml` or `disable_comments = true` in `params.toml`.

## Create a user

To create a new user, please refer to the [Getting Started]({{< relref "get-started.md#introduce-yourself" >}}) guide.

## Create a project

To create a project:

    hugo new  --kind project project/my-project-name

Then edit the newly created file `content/project/my-project-name.md`. Either you can link the project to an external project website by setting the `external_link: "http://external-project.com"` variable at the top of the file, or you can add content (below the final `---`) in order to render a project page on your website.

## Create a talk

To create a talk:

    hugo new  --kind talk talk/my-talk-name

Then edit the newly created file `content/talk/my-talk-name.md` with your full talk title and details. Note that many of the talk parameters are similar to the publication parameters.

## Create slides

Slides can be created very efficiently using Markdown, presented to your audience, and shared on your site. Speaker notes included!

See the [slides demo](https://themes.gohugo.io//theme/academic/slides/example-slides#/) - although note that this demo is hosted by Hugo team and they have modified their demo to reduce functionality. Build the example site (`themes/academic/exampleSite/`) locally to see the full demo including speaker notes.

Refer to the [example slide deck](https://raw.githubusercontent.com/gcushen/hugo-academic/master/exampleSite/content/slides/example-slides.md) at `themes/academic/exampleSite/content/slides/example/index.md` to learn how to get started.

Link slides with a talk or publication by editing the external `url_slides` option or internal `slides` option in the talk/publication page to point to your slides. For example, `slides: "example"` points to the Markdown formatted slide deck in the example site at `slides/example/index.md`. See the full example front matter which includes `url_slides` and `slides` [here](https://raw.githubusercontent.com/gcushen/hugo-academic/master/exampleSite/content/talk/example/index.md).

### Theming a slide deck

Slide decks use their own theming system rather than the one configured in your site's `params.toml`. This enables the theme of each slide deck to be customized in its front matter. 

For a *light* themed slide deck, consider setting the following `slides` options in your slide deck's front matter:

```yaml
slides:
  theme: "white"  # Reveal JS theme name
  highlight_style: "github"  # Highlight JS theme name
```

For a *dark* themed slide deck, consider setting the following `slides` options in your slide deck's front matter:

```yaml
slides:
  theme: "black"  # Reveal JS theme name
  highlight_style: "dracula"  # Highlight JS theme name
```

Note that the *highlight_style* option is only available for slides made with Academic **v4.3.0+**.

## Create a publication

### Automatically

The leading reference management tools enable you to export your publications to the open BibTeX format. If you are new to research we recommend managing references with [Zotero](https://www.zotero.org/), a popular open source tool.

In your reference management tool, create a list of your own publications and export it as a `*.bib` BibTeX file.

Python 3 is a prerequisite, so please [install Python 3](https://realpython.com/installing-python/) if it's not already installed. Also, you should backup your website before continuing, or ensure that it is checked into Git so that you can review the changes that will be proposed by Academic's admin tool later on.

Open your Terminal or Command Prompt app and install Academic's admin tool:

```python
pip3 install -U academic
```

Use the `cd` command to navigate to your website folder in the terminal.

Then import your publications with:

```bash
academic import --bibtex <path_to_your/publications.bib>
```

The tool is in *beta* status and intended purely to help assist you, so the generated output in the `publication` folder should be reviewed prior to publishing your site. You can also consider enhancing the output by taking a look at the front matter parameters in the files alongside the details in the *Manually* section below.

To contribute to the tool or submit feature requests and bug report, please check out the [**Academic admin tool on GitHub**](https://github.com/sourcethemes/academic-admin). 

### Manually

Alternatively, publications can be manually created using the command:

    hugo new --kind publication publication/<my-publication>

where `<my-publication>` is the name of your publication, using hyphens (`-`) instead of spaces.

Then edit the parameters in `content/publication/<my-publication>/index.md` to include the details of your publication. The main parameters include:

- **title:** the title of your publication
- **date:** the date that your publication was first published (must be in a valid TOML date format)
- **publication_types:** use the following legend to specify the type of your publication, e.g. `"1"` for conference proceedings:
  - 0 = Uncategorized
  - 1 = Conference paper
  - 2 = Journal article
  - 3 = Preprint / Working Paper
  - 4 = Report
  - 5 = Book
  - 6 = Book section
  - 7 = Thesis (**v4.2+ required**)
  - 8 = Patent (**v4.2+ required**)
- **publication:** where your title was published - Markdown formatting is enabled here for italic etc.
- **abstract:** the summary of your publication

Further details on your publication can be written in the body of the document (after the YAML/TOML front matter) using *Markdown* for formatting. This text will be displayed on the publication's page.

To enable visitors to read your work, either paste a link to your PDF in `url_pdf` or add a PDF file with the same name as your publication's own folder to your publication's folder and a PDF link will be automatically generated. For example, if your publication is located at `publication/photons/index.md`, place a PDF at `publication/photons/photons.pdf`.

To enable visitors to easily cite your work, export a BibTeX citation file named `cite.bib` from your reference management tool to your publication's own folder and a citation link will be automatically generated.

**Linking other resources**

The `url_` links can either point to local or web content. Associated local publication content, may be copied to the publication's folder and referenced like `url_code = "code.zip"`.

You can also [associate custom link buttons with the publication](#page-resources).

{{% alert warning %}}
Any double quotes (`"`) or backslashes (e.g. LaTeX `\times`) occurring within the value of any frontmatter parameter (such as the *abstract*) should be escaped with a backslash (`\`). For example, the symbol `"` and LaTeX text `\times` become `\"` and `\\times`, respectively. Refer to the [TOML documentation](https://github.com/toml-lang/toml#user-content-string) for more info.
{{% /alert %}}

**Modifying Publication Types**

To rename publication types in v4+, [edit the associated `pub_*` values in your language pack]({{< relref "language.md" >}}). These values can be found in the default [English language pack](
https://github.com/gcushen/hugo-academic/blob/master/i18n/en.yaml) but may not have been translated to all of the other languages packs yet.

To add or remove publication types in v4+, [override]({{< relref "customization.md#override-a-template" >}}) the [layouts/partials/pub_types.html](https://github.com/gcushen/hugo-academic/blob/master/layouts/partials/pub_types.html) file with your own array using the Go templating language.

## Create a course or documentation

The *docs* feature is designed for **knowledge sharing**. Use cases include **online courses, tutorials, software documentation, and knowledge bases**.

[This website is using](https://github.com/sourcethemes/academic-www) the *docs* feature for the purpose of documenting Academic. Also, there is a [online course demo](https://academic-demo.netlify.com/courses/).

Refer to the [example course](https://github.com/gcushen/hugo-academic/tree/master/exampleSite/content/courses) at `themes/academic/exampleSite/content/courses/` to learn how to get started.

Continue reading below to learn more about creating courses, tutorials, and documentation using the *docs* feature.

### Organization

The *docs* feature can be used to create courses, tutorials, and documentation in the following file structure:

```
content/courses
├── _index.md         # Lists your courses, tutorials, or documentation
└── example           # Folder for your course/tutorial/documentation
    ├── _index.md     # Overview of this course/tutorial/documentation
    ├── example1.md   # A page
    └── example2.md   # Another page
└── course2           # Folder for another course/tutorial/documentation
    ├── _index.md
    ├── intro.md
    └── ...
```

File and folder names should not contain spaces (use hyphens instead).

### Renaming

The `courses` folder may be renamed. For example, we can rename it to `docs` for software/project documentation, or `tutorials` for creating an online course.

After renaming or deleting the `courses` folder, you may wish to update any `[[main]]` menu links to it by editing your menu configuration at `config/_default/menus.toml`.

For example, if you delete this folder, you can remove the following from your menu configuration:

```toml
[[main]]
  name = "Courses"
  url = "courses/"
  weight = 50
```

Or, if you are creating a software documentation site, you can rename the `courses` folder to `docs` and update the associated *Courses* menu configuration to:

```toml
[[main]]
  name = "Docs"
  url = "docs/"
  weight = 50
```

### Listing courses and documentation

The `content/courses/_index.md` file automatically lists any course, tutorial, or documentation folders within the `content/courses/` folder. Open the file to edit the page title.

```yaml
title: Courses
layout: docs  # Do not modify.

# Optional header image (relative to `static/img/` folder).
header:
  caption: ""
  image: ""
```

### Course and documentation metadata

Edit the `_index.md` within your course/documentation folder (e.g. `content/courses/example/_index.md`) in order to specify a name and summary for your course/documentation.

```yaml
# Course title, summary, and position in the list.
linktitle: An Example Course
summary: Learn how to use Academic's docs layout for publishing online courses, software documentation, and tutorials.
weight: 1

# Page metadata.
title: Overview
date: "2018-09-09T00:00:00Z"
lastmod: "2018-09-09T00:00:00Z"
draft: false  # Is this a draft? true/false
toc: true  # Show table of contents? true/false
type: docs  # Do not modify.

# Add menu entry to sidebar.
# - name: Declare this menu item as a parent with ID `name`.
# - weight: Position of link in menu.
menu:
  example:
    name: Overview
    weight: 1
```

### Menus

If you use the *docs* layout, note that the name of the menu in the front matter should be in the form `menu: X:` where `X` is the folder name. Hence, if you rename the `courses/example/` folder, you should also rename the menu definitions in the front matter of files within `courses/example/` from `menu: example:` to `menu: <NewFolderName>:`.

Hugo also offers an alternative approach of storing the menu for each course/documentation centrally in `config/_default/menus.toml` rather than in the front matter of each course/documentation page.

Read more about Hugo's menu system [here](https://gohugo.io/content-management/menus/).

### Pages

You can create as many pages as your need. Each page should have a title, menu link (`menu`) to it, and a page `type` of `docs`.

`title` is the page title which appears in page header, whereas `linktitle` is the label for link to this page. If you remove `linktitle`, the menu link will display the page title.

To show a table of contents generated from the headings on your page, set `toc` to `true`.

To show a prev/next pager at the bottom of each docs section page, enable `docs_section_pager` in `params.toml` and then set the order of the pager by defining a `weight` for each page.

An example course/documentation page is as follows:

```yaml
---
title: Example Page 1
linktitle: Tips 1-2
toc: true
type: docs
date: "2019-05-05T00:00:00Z"
draft: false
menu:
  example:
    parent: Example Topic
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

Content...
```

## Manage archive pages

The archive (or *node index*) pages (e.g. `/post/`) are the special pages which list all of your content. They can exist for blog posts, publications, and talks. The homepage widgets will automatically link to the archive pages when you have more items of content than can be displayed in the widget. Therefore, if you don't have much content, you may not see the automatic links yet - but you can also manually link to them using a normal Markdown formatted link in your content.

You can edit the title and add your own content, such as an introduction, by copying the following content `_index.md` files from the example site to the same structure within your `content/` folder:

    /themes/academic/exampleSite/content/post/_index.md
    /themes/academic/exampleSite/content/publication/_index.md
    /themes/academic/exampleSite/content/talk/_index.md
    
Then edit the `title` parameter in each `_index.md` as desired and add any content after the front matter. You will notice that the `_index.md` files differ slightly, with some having special options available for the associated content type. For example, `publication/_index.md` contains an option for setting the citation style of the listings which appear on the publication archive page.

## Removing content

To remove content permanently, simply delete the relevant page file/folder within your `content/` folder.

To temporarily unpublish content, set `draft: true` at the top of a page's front matter.

## View your updated site

After you have made changes to your site, you can view it by running the `hugo server` command and then opening [localhost:1313](http://localhost:1313) in your web browser.

## Deploy your site

Finally, you can [deploy your site]({{< relref "deployment.md" >}}). 
