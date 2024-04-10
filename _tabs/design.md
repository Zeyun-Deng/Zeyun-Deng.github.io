---
# the default layout is 'page'
# layout: home
icon: fas fa-info
order: 6
title: Design
---

<ul>
  {% for post in site.posts %}
    {% if post.categories contains 'Design' %}
      <!-- <li>
        <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
        {% if post.image and post.image.path %}
        <img src="{{ post.image.path }}" alt="{{ post.title }}">
        {% endif %}
      </li> -->
        <article class="card-wrapper card">
            <a href="/posts/{{ post.title | slugify }}" class="post-preview row g-0 flex-md-row-reverse" pcked="1">
                <div class="col-md-5">
                    <div class="preview-img">
                        <img src="{{ post.image.path }}" alt="Preview Image" loading="lazy">
                    </div>
                </div>
                <div class="col-md-7">
                    <div class="card-body d-flex flex-column">
                        <h1 class="card-title my-2 mt-md-0">
                            {{ post.title }}
                        </h1>
                        <div class="card-text content mt-0 mb-3">
                            <!-- 这里的文章内容需要根据实际情况动态插入 -->
                            <p> {{ post.excerpt }} </p>
                        </div>
                        <div class="post-meta flex-grow-1 d-flex align-items-end">
                            <div class="me-auto">
                                <i class="far fa-calendar fa-fw me-1"></i>
                                <time>{{ post.date | date: "%b %d, %Y" }}</time>
                                <i class="far fa-folder-open fa-fw me-1"></i>
                                <span class="categories">{{ post.categories | join: ', ' }}</span>
                            </div>
                        </div>
                    </div>
                </div>
            </a>
        </article>
    {% endif %}
  {% endfor %}
</ul>