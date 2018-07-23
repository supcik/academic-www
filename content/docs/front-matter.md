+++
title = "Front Matter"

date = 2017-12-03
lastmod = 2017-12-03

[menu.docs]
  parent = "content"
  weight = 10
+++

Front matter allows page-specific variables to be included at the top of a Markdown file using [TOML format](https://learnxinyminutes.com/docs/toml/), set between triple-plus `+++` lines. The variables may include metadata such as page title, date published, author, categories, tags, and so on. Here is a simple example:

```toml
+++
date = 2017-12-01
title = "My first blog post"
+++
```
