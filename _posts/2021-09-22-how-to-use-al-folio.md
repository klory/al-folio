---
layout: distill
title: How to use al-folio
description: Explain how to use this awesome theme for beginners
date: 2021-09-22

authors:
  - name: Fangda Han
    url: "https://klory.github.io/"
    # affiliations:
    #   name: Myself

bibliography: distill.bib

---

## Setup environment

The theme is build on Ruby, and if you are using MacOS or don't have root permission, you probably want to install your own Ruby (just like Anaconda for Python if you are a Python user like me). I use [rbenv](https://github.com/rbenv/rbenv){:target="\_blank"}, the steps are as follows:

1. [Install rbenv](https://github.com/rbenv/rbenv#using-package-managers) using brew.
2. [Install your own Ruby](https://github.com/rbenv/rbenv#installing-ruby-versions) using rbenv.
3. Add your own ruby into your `PATH`: e.g. `~/.rbenv/shims:/usr/local/bin:/usr/bin:/bin`
4. Run `which ruby` to verify you're indeed using the Ruby your just installed.
5. Now your can follow [the al-folio instructions](https://github.com/alshedivat/al-folio#local-setup) to setup your own website.

All markdown files support HTML and [Liquid](https://github.com/Shopify/liquid) language.


## Structure

`_config.yml` defines all global variables. If you just started and don't know how to read and use this file, here are some tips.

### Publications

* `_pages/publications.md` shows the content, make sure to change the `years` to contain all your publications. 
* `_bibliography/papers.bib` contains all papers.
* use `@string{aps = {American Physical Society,}}` to select the style.
* use `selected` to tell whether you want it display this paper in the main page.
* use `abbr` to add an abbreviation (for certain styles).
* use `html` to add an html button.
* use `abstract` to add an abstract button.
* use `bibtex_show` to show a BIB button.

### Blogs

* `blog/index.html` shows the content.
* `_posts/*` contains all blogs.
* follow [the al-folio template](https://github.com/alshedivat/al-folio/blob/master/_posts/2018-12-22-distill.md) to use distill format to write your blog.
* `layout` has to be `post` if you want to use Disqus to add comment.

### Projects

* `_includes/projects*.html` define the UI.
* `_pages/projects.md` shows the content.
* `_projects/*` contains all projects.

### News

* `_pages/news.md` shows the content.
* `_news/*` contains all news.


## FAQs

### How to add tables/images/pdf/citations/twitters?

[Al-folio post examples](https://github.com/alshedivat/al-folio/tree/master/_posts)

### How to add your own page?

Create `news.md` in `_pages/`, you can copy `projects.md` as a start, modify the content as your want using HTML and Liquid.