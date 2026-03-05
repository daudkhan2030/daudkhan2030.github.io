---
title: "C++ / Engineering"
layout: single
permalink: /engineering/
author_profile: false
---
{% assign posts = site.categories.engineering %}

{% if posts and posts.size > 0 %}
  {% for post in posts %}
    <h2>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </h2>
    {{ post.excerpt }}
  {% endfor %}
{% else %}
  <p>No posts found in Engineering category.</p>
{% endif %}
