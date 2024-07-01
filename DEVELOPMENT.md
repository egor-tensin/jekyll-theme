Workspace setup
---------------

* To reduce pain, set up [rbenv] to manage your Ruby versions.
Install one that's known to work:

      make ruby

    * Otherwise, make sure you have Ruby and [Bundler] set up.

* Install dependencies:

      make deps

* Make sure builds are working:

      make build

[rbenv]: https://github.com/rbenv/rbenv
[Bundler]: https://bundler.io/

Development
-----------

* Build the example website and serve it at http://localhost:4000/jekyll-theme/:

      make serve

    * It will pick up changes and reload pages automatically.

Upgrading dependencies
----------------------

* To upgrade dependencies in Gemfile.lock & push them to the repository:

      make maintenance

* Manually upgrade dependencies in Gemfile.lock:

      bundle update

Building static pages
---------------------

If you try to copy the _site directory and open index.html without running the
web server, it won't work: all links will be messed up.
Jekyll doesn't provide native support for generating a static website which can
be browsed without running a web server.

One workaround is to `wget` the website:

    make serve LIVE_RELOAD=0    # Live reloading breaks wget
    make wget

The truly static version will be downloaded to the .wget/ directory.

Bootstrap theme
---------------

At one point I decided to bundle a modified version of Bootstrap 3.4 with the
theme.
One thing I found annoying about the unmodified Bootstrap is the small font
size & the insanely large headers.
I used the [customization tool] with a [custom config] to download a modified
Boost version and included it in the assets/bootstrap directory.

[customization tool]: https://getbootstrap.com/docs/3.4/customize/
[custom config]: assets/bootstrap/config.json

TODO: port the theme to Bootstrap 4/5/whatever?
