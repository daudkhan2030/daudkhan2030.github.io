---
layout: single
permalink: /systems/
author_profile: false
---

{% assign posts = site.posts | where_exp: "post", "post.categories contains 'systems'" %}

{% for post in posts %}
  {% include archive-single.html %}
{% endfor %}
