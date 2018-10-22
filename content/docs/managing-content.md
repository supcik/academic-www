+++
date = 2016-04-18
draft = false
title = "Managing content"
math = false
aliases = ["post/managing-content/"]

toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.

[menu.docs]
  parent = "content"
  weight = 20
+++

This is a brief guide to managing content with the Academic framework. Content can include publications, projects, talks, news/blog articles, and widget pages. After you have read this guide about creating and managing content, you may also be interested to learn about [writing content with Markdown, LaTeX, and Shortcodes]({{< relref "writing-markdown-latex.md" >}}).<!--more-->

{{% alert warning %}}
Note that there is a bug in Hugo v0.49 affecting the `hugo new ...` commands on this page. There is a [workaround for Hugo v0.49](https://github.com/gcushen/hugo-academic/issues/732#issuecomment-430049337).
{{% /alert %}}

## Featured image

To display a **featured image** in content pages, simply drag an image named `featured.*` (e.g. `featured.jpg`) into your page's folder.

{{% alert note %}}
If your page does not have its own folder within its section folder, you can refactor a page named `NAME.md` to `NAME/index.md`, creating the folder `NAME`. (Note that this requires Academic v3+ and Hugo v0.48+.)
{{% /alert %}}

Want to caption the image or set the focal point for thumbnails? The parameters below can be added to the bottom of your page front matter to customize the appearance of the image. The caption supports Markdown and can be used to write an image caption or credit. The focal point ensures that automatic resizes of the image keep the subject in view.

```toml
# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
[image]
  # Caption (optional)
  caption = "Photo by [Academic](https://sourcethemes.com/academic/)"

  # Focal point (optional)
  # Options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
  focal_point = "Smart"
```

## Header image

To display a full width **header image** in archive pages (e.g. `YOUR_URL/post/`), the header parameters below can be inserted towards the end of a page's `+++` preamble. It is assumed that the image is located in your `static/img/` folder, so the full path in the example below will be `static/img/header.png`. The `caption` parameter supports Markdown and can be used to write an image caption or credit. 

```toml
[header]
image = "headers/getting-started.png"
caption = "Image credit: [**Academic**](https://github.com/gcushen/hugo-academic/)"

```

## Math and Code

To enable **LaTeX math** rendering for a page, you should include `math = true` in the page's `+++` preamble, as demonstrated in the included example site. Otherwise, to enable math on the homepage or for all pages, you must globally set `math = true` in `config.toml`.

To disable **source code highlighting** for all pages, set `highlight = false` in `config.toml`. You can then enable source code highlighting only on pages that need it by setting `highlight = true` in that page's preamble. See the [code-highlighting docs]({{< relref "writing-markdown-latex.md#code-highlighting" >}}) for more details.

## Page features

The following parameters can be added to the front matter of a page to control its features:

```toml
reading_time = false  # Show estimated reading time?
share = false  # Show social sharing links?
profile = false  # Show author profile?
comments = false  # Show comments?
```

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

The tool is in *beta* status and intended purely to help assist you, so the generated output in the `publications` folder should be reviewed prior to publishing your site. You can also consider enhancing the output by taking a look at the front matter parameters in the files alongside the details in the *Manually* section below.

To contribute to the tool or submit feature requests and bug report, please check out the [**Academic admin tool on GitHub**](https://github.com/sourcethemes/academic-admin). 

### Manually

Alternatively, publications can be manually created using the command:

    hugo new --kind publication publication/<my-publication>

where `<my-publication>` is the name of your publication, using hyphens (`-`) instead of spaces.

Then edit the parameters in `content/publication/<my-publication>/index.md` to include the details of your publication. The main parameters include:

- **title:** the title of your publication
- **date:** the date that your publication was first published (must be in a valid TOML date format)
- **publication_types:** use the legend to specify the type of your publication, e.g. conference proceedings
- **publication:** where your title was published - Markdown formatting is enabled here for italic etc.
- **abstract:** the summary of your publication

Further details on your publication can be written in the body of the document (after the `+++` metadata section ends) using *Markdown* for formatting. This text will be displayed on the publication's page.

To enable visitors to read your work, either paste a link to your PDF in `url_pdf` or add a PDF file with the same name as your publication's own folder to your publication's folder and a PDF link will be automatically generated. For example, if your publication is located at `publication/photons/index.md`, place a PDF at `publication/photons/photons.pdf`.

To enable visitors to easily cite your work, export a BibTeX citation file named `cite.bib` from your reference management tool to your publication's own folder and a citation link will be automatically generated.

**Linking other resources**

The `url_` links can either point to local or web content. Associated local publication content, may be copied to the publication's folder and referenced like `url_code = "code.zip"`.

You can also associate custom link buttons with the publication by adding the following block within the front matter:

```
url_custom = [{name = "Custom Link 1", url = "http://example.org"},
              {name = "Custom Link 2", url = "http://example.org"}]
```

{{% alert warning %}}
Any double quotes (`"`) or backslashes (e.g. LaTeX `\times`) occurring within the value of any frontmatter parameter (such as the *abstract*) should be escaped with a backslash (`\`). For example, the symbol `"` and LaTeX text `\times` become `\"` and `\\times`, respectively. Refer to the [TOML documentation](https://github.com/toml-lang/toml#user-content-string) for more info.
{{% /alert %}}

## Create a blog post

To create a blog/news article:

    hugo new  --kind post post/my-article-name

Then edit the newly created file `content/post/my-article-name.md` with your full title and content.

Hugo will automatically generate summaries of posts that appear on the homepage. If you are dissatisfied with an automated summary, you can either limit the summary length by appropriately placing <code>&#60;&#33;&#45;&#45;more&#45;&#45;&#62;</code> in the article body, or completely override the automated summary by adding a `summary` parameter to the `+++` preamble such that:

    summary = "Summary of my post."

To disable commenting for a specific post, you can add `disable_comments = true` to the post `+++` preamble. Or to disable commenting for all posts, you can either set `disqusShortname = ""` or `disable_comments = true` in `config.toml`.

## Create a project

To create a project:

    hugo new  --kind project project/my-project-name

Then edit the newly created file `content/project/my-project-name.md`. Either you can link the project to an external project website by setting the `external_link = "http://external-project.com"` variable at the top of the file, or you can add content (below the final `+++`) in order to render a project page on your website.

## Create a talk

To create a talk:

    hugo new  --kind talk talk/my-talk-name

Then edit the newly created file `content/talk/my-talk-name.md` with your full talk title and details. Note that many of the talk parameters are similar to the publication parameters.

## Create slides

Slides can be created very efficiently using Markdown, presented to your audience, and shared on your site. Speaker notes included!

See the [slides demo](https://themes.gohugo.io//theme/academic/slides/example-slides#/) - although note that this demo is hosted by Hugo team and they have modified their demo to reduce functionality. Build the example site (`themes/academic/exampleSite/`) locally to see the full demo including speaker notes.

Refer to the [example slide deck](https://raw.githubusercontent.com/gcushen/hugo-academic/master/exampleSite/content/slides/example-slides.md) at `themes/academic/exampleSite/content/slides/example-slides.md` to learn how to get started.

Link slides to a talk or publication by editing the `url_slides` option in the talk/publication page to point to your slides. For example, `url_slides = "slides/example-slides"` points to the slide deck in this example. See the full example front matter which includes `url_slides` [here](https://raw.githubusercontent.com/gcushen/hugo-academic/master/exampleSite/content/talk/example/index.md).

## Create a course or documentation

The *docs* layout is designed for **knowledge sharing**. Use cases include **online courses, tutorials, software documentation, and knowledge bases**.

This website is using the *docs* layout for the purpose of documenting Academic. Also, there is a [online course demo](https://themes.gohugo.io//theme/academic/tutorial/).

Refer to the [example course](https://github.com/gcushen/hugo-academic/tree/master/exampleSite/content/tutorial) at `themes/academic/exampleSite/content/tutorial/` to learn how to get started.

If you are a data analyst/scientist using the **R** language (e.g. *RStudio* and *RMarkdown*), we recommend taking a look at the dedicated [R boilerplate project on GitHub](https://github.com/sourcethemes/project-kickstart-r). 

## Create a widget page

So you would like to create a page which utilizes Academic's widget system, similar to the homepage?

Create a new folder in your `content` folder, naming it with your new page name. In this example, we will create a *tutorials* page by creating a `content/tutorials/` folder.

Within your new `content/tutorials/` folder, create a file named `_index.md` containing the following parameters:

```
+++
title = "Tutorials"  # Add a page title.
date = 2017-01-01T00:00:00  # Add today's date.
widgets = true  # Page type is a Widget Page.
summary = ""  # Add a page description.
+++
```

Install widgets into your `content/tutorials/` folder. To achieve this, widgets can be copied from your `content/home/` folder or downloaded from [Github](https://github.com/gcushen/hugo-academic/tree/master/exampleSite/content/home).

## Create other pages (e.g. CV)

For other types of content, it is possible to create your own custom pages. For example, let's create a `cv.md` page for your Curriculum Vitae in your `content` folder. Copy across the frontmatter from the top of one of your post files, adapting it as necessary, and editing your Markdown content below. You can then link to your new page by adding the code `[My CV]{{</* ref "cv.md" */>}}` to any of your existing content.

Alternatively, for the above example, we could use a PDF of your Curriculum Vitae. For this purpose, create a folder called `files` within your `static` folder and move a PDF file named `cv.pdf` to that location, so we have a `static/files/cv.pdf` file path. The PDF can then be linked to from any content by using the code: `{{%/* staticref "files/cv.pdf" */%}}Download my CV{{%/* /staticref */%}}`.

## Manage archive pages

The archive (or *node index*) pages (e.g. `/post/`) are the special pages which list all of your content. They can exist for blog posts, publications, and talks. The homepage widgets will automatically link to the archive pages when you have more items of content than can be displayed in the widget. Therefore, if you don't have much content, you may not see the automatic links yet - but you can also manually link to them using a normal Markdown formatted link in your content.

You can edit the title and add your own content, such as an introduction, by copying the following content `_index.md` files from the example site to the same structure within your `content/` folder:

    /themes/academic/exampleSite/content/post/_index.md
    /themes/academic/exampleSite/content/publication/_index.md
    /themes/academic/exampleSite/content/talk/_index.md
    
Then edit the `title` parameter in each `_index.md` as desired and add any content after the `+++` preamble/frontmatter ends. You will notice that the `_index.md` files differ slightly, with some having special options available for the associated content type. For example, `publication/_index.md` contains an option for setting the citation style of the listings which appear on the publication archive page.

## Removing content

Generally, to remove content, simply delete the relevant page file/folder from your `content/post`, `content/publication`, `content/project`, or `content/talk` folder.

## View your updated site

After you have made changes to your site, you can view it by running the `hugo server` command and then opening [localhost:1313](http://localhost:1313) in your web browser.

## Deploy your site

Finally, you can [deploy your site]({{< relref "deployment.md" >}}). 
