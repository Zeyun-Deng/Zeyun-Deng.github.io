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
        {% if post.image and post.image.path %}
        <img src="{{ post.image.path }}" alt="{{ post.title }}">
        {% endif %}
      </li>
    {% endif %}
  {% endfor %}
</ul>