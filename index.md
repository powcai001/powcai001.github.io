---
layout: single
title: "主页"
permalink: /
author_profile: true
---

## 📝 最新文章

{% for post in site.posts limit: 10 %}
  <article>
    <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
    <p class="post-meta">
      <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y年%m月%d日" }}</time>
      {% if post.tags.size > 0 %}
        <span class="tags">
          {% for tag in post.tags %}
            <a href="/tags/#{{ tag | slugify }}">{{ tag }}</a>
          {% endfor %}
        </span>
      {% endif %}
    </p>
    {% if post.excerpt %}
      <p>{{ post.excerpt }}</p>
    {% endif %}
  </article>
  <hr>
{% endfor %}

<p><a href="/blog/">查看所有文章 →</a></p>
