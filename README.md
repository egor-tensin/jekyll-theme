jekyll-theme
============

[![Publish](https://github.com/egor-tensin/jekyll-theme/actions/workflows/jekyll.yml/badge.svg)](https://github.com/egor-tensin/jekyll-theme/actions/workflows/jekyll.yml)

My [Jekyll] theme.

I use it for [egor-tensin.github.io], [blog], [sorting-algorithms].

[Jekyll]: https://jekyllrb.com/
[egor-tensin.github.io]: https://github.com/egor-tensin/egor-tensin.github.io
[blog]: https://github.com/egor-tensin/blog/tree/gh-pages
[sorting-algorithms]: https://github.com/egor-tensin/sorting-algorithms/tree/gh-pages

Preview
-------

An example website can be viewed at https://egor-tensin.github.io/jekyll-theme/.

Configuration
-------------

The complete list of configuration options follows.
Put it in \_config.yml and adjust how you see fit.

```
settings:
  project:
    name: Test
    description: This is a test project
    license: MIT License
    license_file: LICENSE.txt
  author:
    name: John Doe
    email: John.Doe@example.com
  navbar:
    hide: false
```

Features
--------

### Layouts

* `plain`: navbar at the top + footer at the bottom
* `default`: same as plain, but with a sidebar on the right.
* `page`: same as default, but with the page's header.
* `post`: same as default, but with the post's header and publication date.

### Navbar

Hide the navbar by setting either `site.settings.navbar.hide` or
`page.navbar.hide` to `true`.

Put a page on the navbar by defining setting `page.navbar.link` to `true` or
a custom HTML string.
Pages are sorted in the ascending order of `page.navbar.priority`.
If a page on the navbar is paginated, set `page.navbar.paginated` to `true` so
that it doesn't appear two or more times.
You can add a glyphicon to the navbar link by settings `page.navbar.icon` to
something like `home`, `envelope`, etc.

### Post feed

See [feed/index.html] for an example of how to easily create a paginated post
feed.
Basically, just include posts/posts.html.

[feed/index.html]: feed/index.html

### Category pages

See [life/index.html] or [work/index.html] for examples of how to create
category pages, with a list of posts belonging to the category.
Basically, just include categories/category.html and set the `category`
parameter to the category's name.

[life/index.html]: life/index.html
[work/index.html]: work/index.html

If you want to create a page with a list of all categories and the posts
belonging to them, see [archive/index.html] for an example.
Simply including categories/categories.html should do the job.

[archive/index.html]: archive/index.html

### Code snippets

See [Test post 3] for an example of how to conveniently embed snippets in your
pages.
Basically, you need to put something like this in the front matter:

```
snippets_root_directory: snippets
snippets_language: c++
snippets:
  hello:
    - hello.hpp
    - hello.cpp
  world:
    - world.hpp
    - world.cpp
```

[Test post 3]: _posts/2021-04-09-test-post3.md

And then you can just format an entire section of snippets using a single
`include`:

```
{% include snippets/section.html section_id='hello' %}
```

The line above would output both hello.hpp and hello.cpp to the page.

### Typesetting math

[MathJax] can be used to typeset mathematics using LaTeX.
To use MathJax, set `mathjax` to `true` in page's front matter.
Then you can do things like this:

```
This is an inline formula: $$y = kx + b$$.
This is a formula in a separate block:

$$
y = kx + b
$$
```

[MathJax]: https://www.mathjax.org/

Behind the scenes, Kramdown transforms these to `\(...\)` and `\[...\]`
sequences, to be processed by MathJax.

History
-------

This theme wasn't built from the ground up, it's a product of concurrent
evolution of my three Jekyll projects.
At one moment I got sick of the code duplication, so I just cloned the most
feature-reached project into this repository (tagged `from_jekyll_project`),
and removed everything that wasn't theme-related.
Then I made some minor tweaks to make it work with the other two projects, and
voilà!

I thought about several alternatives to cloning the whole repository.

1. Simply copying the latest versions of the relevant files would lose their
history.
2. Heavily rewriting repository history using `git filter-branch` or something
like this is painfully hard to get right for me.

License
-------

Distributed under the MIT License.
See [LICENSE.txt] for details.

This theme is build upon the Twitter Bootstrap framework, which is also MIT
Licensed and copyright 2015 Twitter.

[LICENSE.txt]: LICENSE.txt
