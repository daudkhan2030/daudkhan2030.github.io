---
layout: single
permalink: /notes/
author_profile: false
---

{% assign posts = site.posts | where_exp: "post", "post.categories contains 'notes'" %}

{% for post in posts %}
  {% include archive-single.html %}
{% endfor %}
