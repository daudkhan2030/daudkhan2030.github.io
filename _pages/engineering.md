---
title: "C++ / Engineering"
layout: single
permalink: /engineering/
author_profile: false
---
{% assign posts = site.categories.engineering %}

{% if posts and posts.size > 0 %}
  {% for post in posts %}
    <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
    <p>{{ post.excerpt }}</p>
  {% endfor %}
{% else %}
  <p>No posts found in Engineering category.</p>
{% endif %}
