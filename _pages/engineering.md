---
title: "C++ / Engineering"
layout: splash
permalink: /engineering/
author_profile: true
---

{% assign posts = site.posts | where_exp: "post", "post.categories contains 'engineering'" %}

{% for post in posts %}
  {% include archive-single.html %}
{% endfor %}
