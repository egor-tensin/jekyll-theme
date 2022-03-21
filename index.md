---
base: https://egor-tensin.github.io
title: Home page
navbar:
  link: Home
  icon: home
  priority: 1
---
This is a preview for my [Jekyll] theme.
I use it for

* [egor-tensin.github.io],
* [blog],
* [sorting-algorithms],
* [wireguard-config].

**Check out the pages below.**

* [Post feed]({{ '/feed/' | relative_url }})
* [Post w/ MathJax formulas]({{ site.baseurl }}{% post_url 2021-04-08-mathjax %})
* [Post w/ code snippets]({{ site.baseurl }}{% post_url 2021-04-09-snippets %})
* [Post w/ _collapsible_ code snippets]({{ site.baseurl }}{% post_url 2021-04-10-collapsible %})
* [Post w/ shell commands]({{ site.baseurl }}{% post_url 2022-03-21-shell %})

[Jekyll]: https://jekyllrb.com/
[egor-tensin.github.io]: {{ page.base }}
[blog]: {{ page.base }}/blog/
[sorting-algorithms]: {{ page.base }}/sorting-algorithms/
[wireguard-config]: {{ page.base }}/wireguard-config/
