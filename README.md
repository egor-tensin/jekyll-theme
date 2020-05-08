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

### GitHub workarounds

MathJax version 3 is used, which is unsupported by Kramdown (which produces
`<script type="math/tex; ..."` tags, suitable only for MathJax 2).
This is why `math_engine` must be set to `null` in _config.yml in order to make
Kramdown output block formulas wrapped in `$$` and inline formulas in `$`
respectively ([inside `<span class="kdmath">` elements][kramdown issue]).
Because if this, MathJax is additionally customized to recognize `$` as an
inline formula delimiter in _includes/common/mathjax.html.

GitHub Pages [helpfully overrides] the `math_engine` setting in your
_config.yml, hardcoding it to `mathjax` instead of `null` (there's a related
[pull request]).
I couldn't find a better way than to override the setting in the markdown
document itself using

    {::options math_engine="+nil+" /}

[kramdown issue]: https://github.com/gettalong/kramdown/issues/342
[helpfully overrides]: https://help.github.com/en/articles/configuring-jekyll
[pull request]: https://github.com/github/pages-gem/pull/644

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
