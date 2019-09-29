Egor's blog
===========

Egor's blog on programming.
Hosted on [GitHub Pages] at https://egor-tensin.github.io/blog/.

[GitHub Pages]: https://pages.github.com

Prerequisites
-------------

[Jekyll] is used to build a set of static HTML pages from a collection of
templates and resources.
[Bundler] is used to manage project's dependencies.
Make sure you have the `bundler` gem installed; project dependencies can then
be installed by executing

    bundle install

in the project's root directory.

[Jekyll]: https://jekyllrb.com/
[Bundler]: http://bundler.io/

Usage
-----

To run a local web server, execute

    bundle exec jekyll serve --watch --drafts --config _config.yml,_config_dev.yml

in the project's root directory.
You can then review your changes at http://localhost:4000/.

If you can't get Jekyll to properly `--watch` for file modifications on
Windows, try adding `--force_polling` to `jekyll`s options:

    bundle exec jekyll serve --watch --force_polling --drafts --config _config.yml,_config_dev.yml

It might still not work though, but you can always re-run `jekyll` manually.

Note that `_config_dev.yml` is included to rewrite some of the `site` fields
from `_config.yml` during development.
In particular, it

* sets `minified_externals` to `false` so that the properly formatted versions
of external CSS stylesheets and JavaScript files are included instead of the
`min`ified versions,
* sets `include_comments` to `false` to exclude the Disqus comments section
from the posts,
* sets `baseurl` to an empty string so that the website can be accessed from
local web server's root directory (i.e. from http://localhost:4000/ instead of
http://localhost:4000/blog/).

### Access via file://

Jekyll doesn't provide native support for generating a static website which can
be browsed without running an instance of Jekyll's web server.
One easy workaround is to `wget` the website and convert the links:

    wget --convert-links --recursive http://localhost:4000/

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

MathJax version 3 is used, which is unsupported by Kramdown (which produces
`<script type="math/tex; ..."` tags, suitable for MathJax 2.
This is why `math_engine` is set to `null` in _config.yml, making Kramdown
output block formulas wrapped in `$$` and inline formulas in `$` respectively.
MathJax is additionally customized to recognize `$` as an inline formula
delimiter in _includes/common/mathjax.html.

[MathJax]: https://www.mathjax.org/

License
-------

Distributed under the MIT License.
See [LICENSE.txt] for details.

This website is build upon the Twitter Bootstrap framework, which is also MIT
Licensed and copyright 2015 Twitter.

[LICENSE.txt]: LICENSE.txt
