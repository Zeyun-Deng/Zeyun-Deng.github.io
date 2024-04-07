---
# the default layout is 'page'
icon: fas fa-info
order: 5
title: Research
---

<h1>{{ page.title }}</h1>

<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'research' %}
      <li>
        <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
        {{ post.excerpt }}
      </li>
    {% endif %}
  {% endfor %}
</ul>