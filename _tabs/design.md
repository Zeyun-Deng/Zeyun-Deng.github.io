---
# the default layout is 'page'
layout: home
icon: fas fa-info
order: 6
title: Design
---

{% assign design_posts = site.posts | where_exp: "post", "post.categories contains 'Design'" %}

{% assign categories = "" | split: "" %}

{% for post in design_posts %}
  {% assign category = post.categories[1] %}
  {% unless categories[category] %}
    {% assign categories[category] = "" | split: "" %}
  {% endunless %}
  {% assign categories[category] = categories[category] | push: post %}
{% endfor %}

{% for category in categories %}
  <h2>{{ category[0] }}</h2>
  {% for post in category[1] %}
    <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
    {% if post.image and post.image.path %}
      <img src="{{ post.image.path }}" alt="{{ post.title }}">
    {% endif %}
  {% endfor %}
{% endfor %}