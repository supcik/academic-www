+++
title = "Create a site locally"

date = 2016-04-20
toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.
weight = 20

[menu.docs]
  parent = "setup"
  weight = 20
+++

We highly **recommend** the [**one-minute Github/Gitlab install** using your web browser]({{< relref "install.md" >}}) **prior** to following the steps on this page to download and edit your site on your computer.

However, we can also skip the Github/Gitlab install and edit your site directly on your computer, [deploying to your preferred provider]({{< relref "deployment.md" >}}).

You can choose from one of the following methods to install your site on your computer:

* [install on your computer using **Git**](#install-with-git) with the Command Prompt/Terminal app
* [install on your computer by **downloading the ZIP** files](#install-with-zip)
* [install on your computer with **RStudio**](#install-with-rstudio)

[After installing, check out the guide to personalizing your site]({{< relref "get-started.md" >}}).

## Install with Git

Prerequisites:

* [Download and install Git](https://git-scm.com/downloads)
* [Download and install Hugo Extended v0.73](https://gohugo.io/getting-started/installing/#quick-install)
  - Ensure you install the **full** version of Hugo, named **_Hugo Extended_**

Install:

1. [Fork](https://github.com/sourcethemes/academic-kickstart#fork-destination-box) the *Academic Kickstart* repository to create a new website
   * If you already created your site with **Netlify**, then **skip this step**
2. Clone your fork to your computer with Git, **replacing `sourcethemes` in the command below with your GitHub username**:

        git clone https://github.com/sourcethemes/academic-kickstart.git My_Website

3. Initialize the theme:

        cd My_Website
        git submodule update --init --recursive

Now you're ready to [personalize and view your site]({{< relref "get-started.md" >}}).

## Install with ZIP

Prerequisites:

* [Download and install Hugo Extended v0.73](https://gohugo.io/getting-started/installing/#quick-install)
  - Ensure you install the **full** version of Hugo, named **_Hugo Extended_**

Install:

1. [Download](https://github.com/sourcethemes/academic-kickstart/archive/master.zip) and extract *Academic Kickstart*
2. [Download](https://github.com/gcushen/hugo-academic/archive/master.zip) and extract the *Academic theme* files from the `hugo-academic-master` folder to the `themes/academic/` folder in *Academic Kickstart*

Now you're ready to [personalize and view your site]({{< relref "get-started.md" >}}).

## Install with RStudio

1. Follow the [Install with Git](#install-with-git) instructions above if you are confident with Git, or otherwise [Install with ZIP](#install-with-zip).
   - Skip the *Install Hugo* step as we'll use RStudio to install Hugo
2. Open [RStudio](https://www.rstudio.com/products/rstudio/), installing the *Blogdown* and *Hugo* dependencies:

        install.packages("blogdown")
        blogdown::install_hugo(version = "0.73.0", force = TRUE)

3. Open `academic.Rproj` from the *Academic Kickstart* folder in *Step 1*

4. Workaround a [Blogdown bug](https://github.com/rstudio/blogdown/issues/359) by moving `config/_default/config.toml` to `config.toml` at your project root

5. In the RStudio menu bar, choose **Addins > Serve Site** (clicking this button will call `blogdown:::serve_site()`)
   - Paste the local URL which RStudio provides (e.g. http://127.0.0.1:4321) into your web browser to preview your new site
   - Avoid using the integrated RStudio web browser as it is very outdated and buggy

Now you're ready to [personalize your site]({{< relref "get-started.md" >}}).

Note that **R content should be saved with the `.Rmarkdown` file extension** rather than `.Rmd`.

## Demo content

For inspiration, refer to the [Markdown content](https://github.com/gcushen/hugo-academic/tree/master/exampleSite) which powers the [Demo](https://academic-demo.netlify.app/).

If you wish to initialise your site with the demo content, copy the contents of the `themes/academic/exampleSite/` folder to your website root folder, overwriting existing files if necessary. The `exampleSite` folder contains an example config file and content to help you get started. The following command can be used to accomplish this:

```bash
cp -av themes/academic/exampleSite/* .
```

## Unlock rewards

{{% alert thanks %}}
**We're full steam ahead on improving Academic, and we need your help!**

- ☕️ [**Donate a coffee**](https://paypal.me/cushen)
- :heart: [Become a backer on **Patreon** and **unlock rewards**](https://www.patreon.com/cushen) such as stickers
- 💵 [Become a **sponsor** and **advertise your site**](https://www.patreon.com/join/cushen)
- :woman_technologist: [**Contribute** code, PR reviews, documentation, color themes, tutorials, etc.](https://github.com/gcushen/hugo-academic/blob/master/.github/contributing.md)
{{% /alert %}}

## Next steps

[Follow the step by step guide to setup your new site]({{< relref "get-started.md" >}}).
