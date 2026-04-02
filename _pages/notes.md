---
title: "Notes / Learning Log"
layout: single
permalink: /notes/
author_profile: false
---

{% assign posts = site.categories.notes %}

{% for post in posts %}
  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
  <p>{{ post.excerpt }}</p>
{% endfor %}
