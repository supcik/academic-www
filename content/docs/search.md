+++
title = "Search"

date = 2018-07-23
lastmod = 2018-08-01

[menu.docs]
  parent = "setup"
  weight = 50
+++

A search widget can be added to your site to empower your users to search your website content for keywords. A [demo]({{< relref "../#search" >}}) can be found on the homepage of this site. The search engine is curently powered by [Algolia](https://www.algolia.com). Alternative providers may be added in the future.

To enable the search widget:

1. Academic **v2.4+** is required. [Update]({{< relref "/docs/update.md" >}}) if necessary.
1. If `home/search.md` does not exist, copy the file from `themes/academic/exampleSite/home/search.md`
1. In `home/search.md` set `active` to true in order to activate the search widget
1. Register a **free** [Algolia](https://www.algolia.com) account and follow their wizard to create a new search app 
1. Build your site by running the `hugo` command in Terminal or Command Prompt
1. Upload the generated `public/search.json` file to the *Indicies* page in your Algolia dashboard
1. Paste the Algolia *App ID*, *API Key*, and *Index Name* from the *Indicies* and *API Keys* pages of your Algolia Dashboard into the `[params.search.algolia]` section in `config.toml`
1. Under `[params.search]` in `config.toml`, set `engine = 1` to activate the Algolia search engine
1. Serve (or build and upload) your site and test out the shiny new search widget on your home page :smile:

Note that whenever your content changes (e.g. you add a new page), you will need to re-build and re-upload the search index to Algolia.
 
