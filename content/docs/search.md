+++
title = "Search"

date = 2018-07-23

[menu.docs]
  parent = "setup"
  weight = 50
+++

A search widget can be added to your site to empower your users to search your website content for keywords. A [demo](http://localhost:1313/academic/#search) can be found on the homepage of this site. The search engine is curently powered by [Algolia](https://www.algolia.com). Alternative providers may be added in the future.

To enable the search widget:

1. Update Academic to **v2.4+** (or grab the latest master version from GitHub). Ensure that you have the search options added to your `config.toml` (scroll down to `config.toml` at [Update bb3adc1](https://github.com/gcushen/hugo-academic/commit/bb3adc17813f4126b80723504aec934d0c8cf8a9) to see the search options that were added in v2.4)
2. In `home/search.md` set `active` to true in order to activate the search widget
3. Register a **free** [Algolia](https://www.algolia.com) account and follow their wizard to create a new search app 
4. Build your site by running the `hugo` command in Terminal or Command Prompt
5. Upload the generated `public/search.json` file to the *Indicies* page in your Algolia dashboard
6. Paste the Algolia *App ID*, *API Key*, and *Index Name* from the *Indicies* and *API Keys* pages of your Algolia Dashboard into the `[params.search.algolia]` section in `config.toml`
7. Under `[params.search]` in `config.toml`, set `engine = 1` to activate the Algolia search engine
8. Serve (or build and upload) your site and test out the shiny new search widget on your home page :smile:

Note that whenever your content changes (e.g. you add a new page), you will need to re-build and re-upload the search index to Algolia.
 
