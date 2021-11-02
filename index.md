---
base: https://egor-tensin.github.io/
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

**Check these out**:

* [posts feed]({{ '/feed/' | relative_url }}),
* [post with MathJax formulas]({{ site.baseurl }}{% post_url 2021-04-08-mathjax %}),
* [post with code snippets]({{ site.baseurl }}{% post_url 2021-04-09-snippets %}),
* [post with collapsible code snippets]({{ site.baseurl }}{% post_url 2021-04-10-collapsible %}).

[Jekyll]: https://jekyllrb.com/
[egor-tensin.github.io]: {{ page.base }}
[blog]: {{ page.base }}/blog/
[sorting-algorithms]: {{ page.base }}/sorting-algorithms/
[wireguard-config]: {{ page.base }}/wireguard-config/
