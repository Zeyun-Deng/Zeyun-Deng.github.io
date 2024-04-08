---
# the default layout is 'page'
icon: fas fa-info
order: 5
title: Research
---

<ul>
  {% for post in site.posts %}
    {% if post.categories contains 'Research' %}
      <li>
        <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
        <!-- {{ post.excerpt }} -->
        {{ post.image }}
      </li>
    {% endif %}
  {% endfor %}
</ul>