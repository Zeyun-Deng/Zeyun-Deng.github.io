---
# the default layout is 'page'
# layout: home
icon: fas fa-info
order: 6
title: Design
---

{% include lang.html %}

{% assign pinned = site.posts | where: 'pin', 'true' %}
{% assign default = site.posts | where_exp: 'item', 'item.pin != true and item.hidden != true' %}

{% assign posts = '' | split: '' %}

<!-- Get pinned posts -->

{% assign offset = paginator.page | minus: 1 | times: paginator.per_page %}
{% assign pinned_num = pinned.size | minus: offset %}

{% if pinned_num > 0 %}
  {% for i in (offset..pinned.size) limit: pinned_num %}
    {% assign posts = posts | push: pinned[i] %}
  {% endfor %}
{% else %}
  {% assign pinned_num = 0 %}
{% endif %}

<!-- Get default posts -->

{% assign default_beg = offset | minus: pinned.size %}

{% if default_beg < 0 %}
  {% assign default_beg = 0 %}
{% endif %}

{% assign default_num = paginator.posts | size | minus: pinned_num %}
{% assign default_end = default_beg | plus: default_num | minus: 1 %}

{% if default_num > 0 %}
  {% for i in (default_beg..default_end) %}
    {% assign posts = posts | push: default[i] %}
  {% endfor %}
{% endif %}

<!-- Filter posts by category 'design' -->

{% assign posts = posts | where_exp: 'item', 'item.categories contains "design"' %}

<div id="post-list" class="flex-grow-1 px-xl-1">
  {% for post in posts %}
    <article class="card-wrapper card">
      <!-- The rest of your code remains unchanged -->
