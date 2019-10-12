+++
title = "Troubleshooting"
summary = """Troubleshoot common issues."""
date = 2016-04-10

toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.
weight = 170
+++

Some common questions and answers are listed below.

**I cloned/downloaded Academic but Hugo produces errors when using it with my existing Hugo site**

Academic is a website *framework* rather than just a *theme*. Please follow the step-by-step guide on the Installation and Getting Started pages of the documentation.
 
If you experience issues, first try running Hugo on the Academic Demo Site found in the `themes/academic/exampleSite` folder and then compare the configuration parameters in the demo site's `config/` folder and front matter of content files with the files in your site.

**Hosting your site with Netlify or Cloudflare and experience strange behavior such as filters not working?**

Disable post-processing steps such as *minification* in your Netlify/Cloudflare admin panel.

**Publications and other content are not sorted by newest first**

Hugo requires a valid date field, as per the front matter of the Demo publications in `themes/academic/content/publication/`. If you wish to display a partial date, such as just the year, a full valid date should still be entered in the front matter - the Customization page describes how to change the format in which dates are displayed on your site.
