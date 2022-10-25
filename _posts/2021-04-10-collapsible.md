---
title: Collapsible snippets
category: Code
snippets_root_directory: snippets
snippets_language: c++
snippets_collapsible: true
snippets:
  hello:
    - hello.hpp
    - hello.cpp
  world:
    - world.hpp
    - world.cpp
---
Snippets are defined in exactly the same way as in the [other post].
Just set a front matter value to make them collapsible, and voilà!

[other post]: {{ site.baseurl }}{% post_url 2021-04-09-snippets %}

{% include jekyll-theme/snippets/section.html section_id='hello' %}

This is another set of snippets:

{% include jekyll-theme/snippets/section.html section_id='world' %}
