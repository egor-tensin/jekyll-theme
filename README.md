jekyll-theme
============

[![CI](https://github.com/egor-tensin/jekyll-theme/actions/workflows/ci.yml/badge.svg)](https://github.com/egor-tensin/jekyll-theme/actions/workflows/ci.yml)

My [Jekyll] theme.

I use it for [egor-tensin.github.io], [blog], [sorting-algorithms].

[Jekyll]: https://jekyllrb.com/
[egor-tensin.github.io]: https://egor-tensin.github.io/
[blog]: https://egor-tensin.github.io/blog/
[sorting-algorithms]: https://egor-tensin.github.io/sorting-algorithms/

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

Put a page on the navbar by setting `page.navbar.link` to `true` or a custom
HTML string.
Pages are sorted in the ascending order of `page.navbar.priority`.
If a page on the navbar is paginated, set `page.navbar.paginated` to `true` so
that it doesn't appear more than once.
You can add a glyphicon to the navbar link by settings `page.navbar.icon` to
something like `home` or `envelope` (or [any other glyphicon]).

[any other glyphicon]: https://getbootstrap.com/docs/3.4/components/#glyphicons

#### GitHub link

If you use `jekyll-github-metadata` (you do if you use the `github-pages` gem),
a link to the GitHub repository is added at the end of the navbar.
Customize the link text and the icon by setting
`site.settings.navbar.github.link` and `site.settings.navbar.github.icon`
accordingly.

Hide the link by settings `site.settings.navbar.github` to `false`.

### Posts feed

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

See [this post][snippets] for an example of how to conveniently embed code
snippets in your pages.
Basically, you need to put something like this in the front matter:

[snippets]: _posts/2021-04-09-snippets.md

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

And then you can just format an entire section of snippets using a single
`include`:

```
{% include snippets/section.html section_id='hello' %}
```

The line above would output both hello.hpp and hello.cpp to the page.

Code snippets can be hidden in collapsible panels.
See [this post][collapsible] for an example.

[collapsible]: _posts/2021-04-10-collapsible.md

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

See [this post][mathjax post] for a usage example.

[mathjax post]: _posts/2021-04-08-mathjax.md

### Custom CSS & JavaScript

Include custom CSS stylesheets in the header & custom JavaScript files in the
footer by specifying the `page.custom_css` and `page.custom_js` arrays.
They will be picked up from the root "assets/css" and "assets/js" directories
respectively (unless the URL is absolute).

History
-------

This theme wasn't built from the ground up, it's a product of concurrent
evolution of my three Jekyll projects.
At one point I got sick of the code duplication, so I just cloned the most
feature-reached project into this repository (tagged `from_jekyll_project`),
and removed everything that wasn't theme-related.
Then I made some minor tweaks to make it work with the other two projects, and
voilà!

I thought about several alternatives to cloning the whole repository.

1. Simply copying the latest versions of the relevant files would lose their
history.
2. Heavily rewriting repository history using `git filter-branch` or something
like this is painfully hard to get right for me.

Development
-----------

### Bootstrap theme

At one point I decided to bundle a modified version of Bootstrap 3.4 with the
theme.
One thing I found annoying about the unmodified Bootstrap is the small font
size & the insanely large headers.
I used the [customization tool] with a [custom config] to download a modified
Boost version and included it in the assets/bootstrap directory.

[customization tool]: https://getbootstrap.com/docs/3.4/customize/
[custom config]: assets/bootstrap/config.json

TODO: port the theme to Bootstrap 4/5/whatever?

License
-------

Distributed under the MIT License.
See [LICENSE.txt] for details.

This theme is build upon the Twitter Bootstrap framework, which is also MIT
Licensed and copyright 2015 Twitter.

[LICENSE.txt]: LICENSE.txt
