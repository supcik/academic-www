+++
title = "Update"

date = 2016-04-20
lastmod = 2017-12-26
draft = false

[menu.docs]
    parent = "setup"
    weight = 11
+++

Feel free to *star* the project on [Github](https://github.com/gcushen/hugo-academic/) to help keep track of updates and check out the [release notes](/academic/updates/) prior to updating your site.

Before updating the framework, it is recommended to make a backup of your entire website directory (or at least your `themes/academic` directory) and record your current version number.

Please follow the method below which corresponds to how you originally installed Academic:

## If you installed `academic-kickstart`

By default, Academic is installed as a Git sub-module which can be updated by running the following command:

```bash
git submodule update --remote --merge
```

## If you installed by Git cloning `hugo-academic`

Before updating for the first time, the remote *origin* repository should be renamed to *upstream*:

    $ cd themes/academic
    $ git remote rename origin upstream

To list available updates:

    $ cd themes/academic
    $ git fetch upstream
    $ git log --pretty=oneline --abbrev-commit --decorate HEAD..upstream/master

Then, update by running:

    $ git pull upstream

## If you installed from a ZIP

Uninstall your current version of Academic by deleting the contents of `themes/academic/`. [Download](https://github.com/gcushen/hugo-academic/archive/master.zip) and extract the latest version of Academic to your `themes/academic/` folder.

## Troubleshooting

Check out the [release notes](/academic/updates/) for the version that you are updating to, paying attention to the breaking changes.

If there are any issues after updating, you may wish to compare your site with the latest [example site](https://github.com/gcushen/hugo-academic/tree/master/exampleSite) to check if any settings changed in `config.toml` or the `+++` front matter of content files.

If you have modified files in `themes/academic`, git will attempt to auto-merge changes. If conflicts are reported, you will need to manually edit the files with conflicts and add them back (`git add <filename>`).
