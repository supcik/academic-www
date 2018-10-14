+++
title = "Front Matter"

date = 2017-12-03
lastmod = 2017-12-03

toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.

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

## RStudio

Alternatively, if you are using RStudio to edit your site and wish to include an RMarkdown file, you'll need to utilise YAML in your RMarkdown file as RMarkdown does not yet support the TOML format. Thus, your RMarkdown front matter will appear similar to below, set between triple-minus `---` lines

```yaml
---
date: 2017-12-01
title: My first blog post
---
```
