---
layout: default
title: Home
---

<div align="center">

Here you will find blogs and posts from the perspective of a junior dev. While most of my wisdom is likely questionable and ill advised, I hope my struggles, learning, and growth can provide clarity to those who read.  

The posts you will find will range from projects I create, opinion blogs, and even self reflection. Take what you find with a grain of salt and hint of humor.  

If you wish to reach out to me, please do so via email (amart89531@gmail.com) or via LinkedIn. I am happy to help out anyone in anyway I can!

<br><br>

<strong>DISCLAIMER: None of the text / referenced code is generated or involves LLMs in any capacity. While they are very helpful, the purpose of this blog is to maximize learning!</strong>

</div>

<div class="post-section">

  <h2 class="post-section-title">Latest Post</h2>
  {% assign latest_post = site.posts | first %}
  {% if latest_post %}
    <a href="{{ latest_post.url }}" class="post-preview-link">
      {% if latest_post.gif %}
        <img src="{{ latest_post.gif }}" alt="{{ latest_post.title }} preview">
      {% endif %}
      <div class="post-info">
        <h2>{{ latest_post.title }}</h2>
        <p class="post-date">{{ latest_post.date | date: "%B %d, %Y" }}</p>
        <p>{{ latest_post.excerpt | strip_html | truncate: 150 }}</p>
      </div>
    </a>
  {% endif %}

  <h2 class="post-section-title">Featured Post</h2>
  {% assign featured_post = site.posts | where: "featured", true | first %}
  {% if featured_post %}
    <a href="{{ featured_post.url }}" class="post-preview-link">
      {% if featured_post.gif %}
        <img src="{{ featured_post.gif }}" alt="{{ featured_post.title }} preview">
      {% endif %}
      <div class="post-info">
        <h2>{{ featured_post.title }}</h2>
        <p class="post-date">{{ featured_post.date | date: "%B %d, %Y" }}</p>
        <p>{{ featured_post.excerpt | strip_html | truncate: 150 }}</p>
      </div>
    </a>
  {% endif %}

</div>

<div class="newsletter-box">
  <h2>Join The Newsletter</h2>
  <p>Get updates on new posts, projects, and behind-the-scenes content.</p>

  <form action="/newsletter" method="POST" class="newsletter-form">
    <input 
      type="email" 
      name="email" 
      placeholder="Enter your email..." 
      required 
    />
    <button type="submit">Subscribe</button>
  </form>
</div>

