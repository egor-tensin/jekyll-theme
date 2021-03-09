jekyll-theme
============

My [Jekyll] theme.

I use it for [egor-tensin.github.io], [blog], [sorting-algorithms].

[Jekyll]: https://jekyllrb.com/
[egor-tensin.github.io]: https://github.com/egor-tensin/egor-tensin.github.io
[blog]: https://github.com/egor-tensin/blog/tree/gh-pages
[sorting-algorithms]: https://github.com/egor-tensin/sorting-algorithms/tree/gh-pages

API
---

See the _config.yml files in the projects above to see which `site` values are
used.
Otherwise this theme is irrelevant for anybody but me of course, so it's not
worth documenting.

Typesetting math
----------------

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
