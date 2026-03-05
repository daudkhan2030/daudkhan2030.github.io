---
title: "Algorithms & CS"
layout: archive
permalink: /algorithms/
author_profile: false
---
{% assign posts = site.posts | where_exp: "post", "post.categories contains 'algorithms'" %}

{% for post in posts %}
  {% include archive-single.html %}
{% endfor %}
