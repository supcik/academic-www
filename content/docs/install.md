+++
title = "Install"

date = 2016-04-20
lastmod = 2018-01-20
draft = false

toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.

[menu.docs]
  parent = "setup"
  weight = 1
+++

You can choose from one of the following four methods to install:

* one-click install using your web browser (recommended)
* install on your computer using Git with the Command Prompt/Terminal app
* install on your computer by downloading the ZIP files
* install on your computer with RStudio

[Hugo v0.48+](https://gohugo.io/getting-started/installing/) is required if installing on your computer.

## Install with web browser

1. [Install Academic with Netlify](https://app.netlify.com/start/deploy?repository=https://github.com/sourcethemes/academic-kickstart)
    * Netlify will provide you with a customizable URL to access your new site
2. On GitHub, go to your newly created `academic-kickstart` repository and edit `config.toml` to personalize your site. Shortly after saving the file, your site will automatically update
3. Read the [Quick Start Guide]({{< relref "get-started.md" >}}) to learn how to add Markdown content. For inspiration, refer to the [Markdown content](https://github.com/gcushen/hugo-academic/tree/master/exampleSite) which powers the [Demo](https://themes.gohugo.io/theme/academic/)

## Install with Git

Prerequisites:

* [Download and install Git](https://git-scm.com/downloads)
* [Download and install Hugo](https://gohugo.io/getting-started/installing/#quick-install)

1. [Fork](https://github.com/sourcethemes/academic-kickstart#fork-destination-box) the *Academic Kickstart* repository and clone your fork with Git: 

        git clone https://github.com/sourcethemes/academic-kickstart.git My_Website
    
    *Note that if you forked Academic Kickstart, the above command should be edited to clone your fork, i.e. replace `sourcethemes` with your GitHub username.*

2. Initialize the theme:

        cd My_Website
        git submodule update --init --recursive

## Install with ZIP

1. [Download](https://github.com/sourcethemes/academic-kickstart/archive/master.zip) and extract *Academic Kickstart*
2. [Download](https://github.com/gcushen/hugo-academic/archive/master.zip) and extract the *Academic theme* to the `themes/academic/` folder from the above step

## Install with RStudio

In RStudio IDE, install the *Blogdown (v0.2+)* and *Hugo* dependencies:

```r
install.packages("blogdown")
blogdown::install_hugo()
```

Now restart RStudio and you can create an Academic project directly from the menu `File -> New Project -> New Directory` - see Figures 1 and 2 below:

{{< figure src="img/docs/rstudio-create-project.png" title="Create project" >}}
{{< figure src="img/docs/rstudio-project-type.png" title="Choose *website using Blogdown* as the project type" >}}

Enter `gcushen/hugo-academic` as the theme:

{{< figure src="img/docs/rstudio-theme.png" title="Choose the Academic theme" >}}

Then you will see a panel in RStudio named *Build* containing a *Build Website* button. When you click this button, RStudio will call `blogdown::build_site()` to build the website, automatically generating files in the `public/` folder.

Use `blogdown::serve_site()` to preview your site in your web browser. We recommend previewing your site in your normal web browser as the in-built RStudio web browser is very outdated and buggy.

## Demo content

For inspiration, refer to the [Markdown content](https://github.com/gcushen/hugo-academic/tree/master/exampleSite) which powers the [Demo](https://themes.gohugo.io/theme/academic/).

If you wish to initialise your site with the demo content, copy the contents of the `themes/academic/exampleSite/` folder to your website root folder, overwriting existing files if necessary. The `exampleSite` folder contains an example config file and content to help you get started. The following command can be used to accomplish this:

```bash
cp -av themes/academic/exampleSite/* .
```

