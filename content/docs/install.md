+++
title = "Install"

date = 2016-04-20
toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.

[menu.docs]
  parent = "setup"
  weight = 1
+++

You can choose from one of the following four methods to install:

* [**one-click install** using your web browser](#install-with-web-browser) **(recommended)**
* [install on your computer using **Git**](#install-with-git) with the Command Prompt/Terminal app
* [install on your computer by **downloading the ZIP** files](#install-with-zip)
* [install on your computer with **RStudio**](#install-with-rstudio)

[After installing, check out the guide to personalizing your site]({{< relref "get-started.md" >}}).

## Install with web browser

1. [Install Academic with Netlify](https://app.netlify.com/start/deploy?repository=https://github.com/sourcethemes/academic-kickstart)
    * Netlify will provide you with a customizable URL to access your new site
2. On GitHub, go to your newly created `academic-kickstart` repository and [personalize your site by editing the files in]({{< relref "get-started.md" >}}) `config/_default/`
   - Shortly after saving (i.e. *committing* a file), your site will automatically update
3. Read the [Widgets]({{< relref "page-builder.md" >}}) and [Content]({{< relref "managing-content.md" >}}) guides to learn how to add widgets and content. For inspiration, refer to the [Markdown content](https://github.com/gcushen/hugo-academic/tree/master/exampleSite) which powers the [Demo](https://academic-demo.netlify.com/)

## Install with Git

Prerequisites:

* [Download and install Git](https://git-scm.com/downloads)
* [Download and install Hugo v0.53+](https://gohugo.io/getting-started/installing/#quick-install)

Install:

1. [Fork](https://github.com/sourcethemes/academic-kickstart#fork-destination-box) the *Academic Kickstart* repository and clone your fork with Git: 

        git clone https://github.com/sourcethemes/academic-kickstart.git My_Website
    
    *Note that if you forked Academic Kickstart, the above command should be edited to clone your fork, i.e. replace `sourcethemes` with your GitHub username.*

2. Initialize the theme:

        cd My_Website
        git submodule update --init --recursive

Now you're ready to [personalize and view your site]({{< relref "get-started.md" >}}).

## Install with ZIP

Prerequisites:

* [Download and install Hugo v0.53+](https://gohugo.io/getting-started/installing/#quick-install)

Install:

1. [Download](https://github.com/sourcethemes/academic-kickstart/archive/master.zip) and extract *Academic Kickstart*
2. [Download](https://github.com/gcushen/hugo-academic/archive/master.zip) and extract the *Academic theme* files from the `hugo-academic-master` folder to the `themes/academic/` folder in *Academic Kickstart*

Now you're ready to [personalize and view your site]({{< relref "get-started.md" >}}).

## Install with RStudio

1. Follow the [Install with Git](#install-with-git) instructions above if you are confident with Git, or otherwise [Install with ZIP](#install-with-zip).
   - Skip the *Install Hugo* step as we'll use RStudio to install Hugo
2. Open [RStudio](https://www.rstudio.com/products/rstudio/), installing the *Blogdown* and *Hugo* dependencies:

    ```r
    install.packages("blogdown")
    blogdown::install_hugo()
    ```

3. Open `academic.Rproj` from the *Academic Kickstart* folder in *Step 1*

4. Workaround a [Blogdown bug](https://github.com/rstudio/blogdown/issues/359) by moving `config/_default/config.toml` to `config.toml` at your project root

5. In the RStudio menu bar, choose **Addins > Serve Site** (clicking this button will call `blogdown:::serve_site()`)
   - Paste the local URL which RStudio provides (e.g. http://127.0.0.1:4321) into your web browser to preview your new site
   - Avoid using the integrated RStudio web browser as it is very outdated and buggy

Now you're ready to [personalize your site]({{< relref "get-started.md" >}}).

Note that **R content should be saved with the `.Rmarkdown` file extension** rather than `.Rmd`.

## Demo content

For inspiration, refer to the [Markdown content](https://github.com/gcushen/hugo-academic/tree/master/exampleSite) which powers the [Demo](https://academic-demo.netlify.com/).

If you wish to initialise your site with the demo content, copy the contents of the `themes/academic/exampleSite/` folder to your website root folder, overwriting existing files if necessary. The `exampleSite` folder contains an example config file and content to help you get started. The following command can be used to accomplish this:

```bash
cp -av themes/academic/exampleSite/* .
```

## Next steps

[Follow the step by step guide to setup your new site]({{< relref "get-started.md" >}}).
