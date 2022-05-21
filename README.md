Jekyll theme
============

[![CI](https://github.com/egor-tensin/jekyll-theme/actions/workflows/ci.yml/badge.svg)](https://github.com/egor-tensin/jekyll-theme/actions/workflows/ci.yml)

My [Jekyll] theme.

I use it for [egort.name], [blog], [sorting-algorithms], [wireguard-config].

[Jekyll]: https://jekyllrb.com/
[egort.name]: https://egort.name/
[blog]: https://egort.name/blog/
[sorting-algorithms]: https://egort.name/sorting-algorithms/
[wireguard-config]: https://egort.name/wireguard-config/

Preview
-------

An example website can be viewed at https://egort.name/jekyll-theme/.

Usage
-----

Use the `jekyll-remote-theme` plugin.
Put this in your \_config.yml:

```
plugins:
  - jekyll-remote-theme
  # Other plugins...

remote_theme: egor-tensin/jekyll-theme
# Preferably, pin the exact commit:
#remote_theme: egor-tensin/jekyll-theme@COMMIT_HASH
```

Configuration
-------------

The complete list of configuration options follows.
Put it in \_config.yml and adjust how you see fit.

```
settings:
  project:
    name: Test project
    # The following settings are picked up from GitHub by default.
    description: This is a test project
    license: MIT License
    license_file: LICENSE.txt
  author:
    name: John Doe
    email: John.Doe@example.com
  navbar:
    hide: false
    # Only relevant if the project's on GitHub.
    github:
      link: GitHub
      icon: globe
  sidebar:
    hide: false
  # If you want to enable Google Analytics, optional:
  ga_tag: X-XXXXXXXXXX
```

Features
--------

* [Layouts](#layouts)
* [Navbar](#navbar)
* [Sidebar](#sidebar)
* [Feed](#feed)
* [Categories](#categories)
* [Code snippets](#code-snippets)
* [Shell commands](#shell-commands)
* [Typesetting math](#typesetting-math)
* [Custom CSS & JavaScript](#custom-css--javascript)

### Layouts

* `plain`: navbar at the top + footer at the bottom.
* `default`: same as plain, but with a sidebar on the right.
* `page`: same as default, but with the page's header.
* `nosidebar`: same as page, but without the sidebar.
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
something like "home" or "envelope" (or [any other glyphicon]).

[any other glyphicon]: https://getbootstrap.com/docs/3.4/components/#glyphicons

#### GitHub link

If you use `jekyll-github-metadata` (you do if you use the `github-pages` gem),
a link to the GitHub repository is added at the end of the navbar.
Customize the link text and the icon by setting
`site.settings.navbar.github.link` and `site.settings.navbar.github.icon`
accordingly.

Hide the link by setting `site.settings.navbar.github` to `false`.

### Sidebar

Hide the sidebar by setting either `site.settings.sidebar.hide` or
`page.sidebar.hide` to `true`.

The sidebar includes two entries by default: "About" and "Latest posts".
Hide them individually by setting `sidebar.{about,latest_posts}.hide` to `true`
(either under `site.settings` or `page`).

Add content to the sidebar by putting it in your _includes/custom-sidebar.html.

### Feed

See [feed/index.html] for an example of how to easily create a paginated post
feed.
Basically, just include posts/feed.html.

[feed/index.html]: feed/index.html

For this to work, you must enable the `jekyll-paginate` plugin.
Don't forget to set `site.paginate_path` to a proper URL (with the `:num`
placeholder) in \_config.yml, like `/feed/page:num/` or something.

### Categories

See [life/index.html] or [work/index.html] for examples of how to create
category pages, with a list of posts belonging to the category.
Basically, just include categories/category.html and set the `category`
parameter to the category's name.

[life/index.html]: life/index.html
[work/index.html]: work/index.html

If you want to create a page with a list of all categories and the posts
belonging to them, see [archive/index.html] for an example.
Simply including categories/all.html should do the job.

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
{% include jekyll-theme/snippets/section.html section_id='hello' %}
```

The line above would output both hello.hpp and hello.cpp to the page.

Code snippets can be hidden in collapsible panels.
See [this post][collapsible] for an example.

[collapsible]: _posts/2021-04-10-collapsible.md

### Shell commands

See [this post][shell] for an example of adding pretty shell commands and their
outputs to a page.
The gist is:

[shell]: _posts/2022-03-21-shell.md

```
{% include jekyll-theme/shell.html cmd='echo 123' out='123' %}
```

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

Add custom `<link>` tags to the header by adding them either to:

* `site.settings.links` in _config.yml (the new links will be added to all
pages),

      settings:
        links:
          - {rel: stylesheet, href: 'https://example.com/global-link.css'}
          - {rel: stylesheet, href: 'assets/css/local-link.css'}

* `page.links` in a page's front matter (will be added to this page only).

      ---
      links:
        - {rel: stylesheet, href: 'https://example.com/global-link.css'}
        - {rel: stylesheet, href: 'assets/css/local-link.css'}
      ---

You can also add custom `<script>` tags in a similar way.

* In _config.yml:

      settings:
        scripts:
          - {src: 'https://example.com/global-script.js'}
          - {src: 'assets/js/local-script.js'}

* In page's front matter:

      ---
      scripts:
        - {src: 'https://example.com/global-script.js'}
        - {src: 'assets/js/local-script.js'}
      ---

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
