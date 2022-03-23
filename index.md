---
base: https://egor-tensin.github.io
title: Home page
layout: plain
navbar:
  link: Home
  priority: 1
---
jekyll-theme
============

---

<div style="display: flex; flex-wrap: wrap; column-gap: 1em;">

<div class="list-group wide-enough">
  <div class="list-group-item disabled">
    <h4 class="list-group-item-heading">features</h4>
  </div>
  <a href="{{ '/feed/' | relative_url }}" class="list-group-item">
    <h4 class="list-group-item-heading">feed</h4>
    <p class="list-group-item-text">A paginated post feed</p>
  </a>
  <a href="{{ '/archive/' | relative_url }}" class="list-group-item">
    <h4 class="list-group-item-heading">categories</h4>
    <p class="list-group-item-text">List of post categories (includes links to each category's page)</p>
  </a>
  <a href="{{ site.baseurl }}{% post_url 2021-04-09-snippets %}" class="list-group-item">
    <h4 class="list-group-item-heading">code snippets</h4>
    <p class="list-group-item-text">Easily include code snippets in your posts</p>
  </a>
  <a href="{{ site.baseurl }}{% post_url 2021-04-10-collapsible %}" class="list-group-item">
    <h4 class="list-group-item-heading">collapsible snippets</h4>
  </a>
  <a href="{{ site.baseurl }}{% post_url 2022-03-21-shell %}" class="list-group-item">
    <h4 class="list-group-item-heading">shell commands</h4>
    <p class="list-group-item-text">Clearly separate shell commands and their outputs from one another</p>
  </a>
  <a href="{{ site.baseurl }}{% post_url 2021-04-08-mathjax %}" class="list-group-item">
    <h4 class="list-group-item-heading">typesetting math</h4>
  </a>
</div>

<div style="flex: 1; min-width: 250px;" markdown="1">

This is a preview for my [Jekyll] theme.
I use it for

* [egor-tensin.github.io],
* [blog],
* [sorting-algorithms],
* [wireguard-config].

You can check out the available features if you follow the links on this page.

[Jekyll]: https://jekyllrb.com/
[egor-tensin.github.io]: {{ page.base }}
[blog]: {{ page.base }}/blog/
[sorting-algorithms]: {{ page.base }}/sorting-algorithms/
[wireguard-config]: {{ page.base }}/wireguard-config/

</div>
</div>
