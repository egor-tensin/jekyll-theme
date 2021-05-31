---
title: Collapsible snippets
excerpt: >
  Snippets can be hidden in collapsible panels.
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
Just set a front matter value, and voilà!

{% include snippets/section.html section_id='hello' %}

This is another set of snippets:

{% include snippets/section.html section_id='world' %}
