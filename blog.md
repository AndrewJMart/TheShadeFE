---
layout: default
title: Blog
---

{% for post in site.posts %}
  <a href="{{ post.url }}" class="post-preview-link">
    <div class="post-preview">
      {% if post.gif %}
        <img src="{{ post.gif }}" alt="{{ post.title }} preview">
      {% endif %}
      <div class="post-info">
        <h2>{{ post.title }}</h2>
        <p class="post-date">{{ post.date | date: "%B %d, %Y" }}</p>
        <p>{{ post.excerpt }}</p>
      </div>
    </div>
  </a>
{% endfor %}

