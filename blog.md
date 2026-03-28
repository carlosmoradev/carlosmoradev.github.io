---
layout: page
title: Blog
permalink: /blog/
---

<div class="section-title">
  <h1>Technical Writing</h1>
</div>

<p style="text-align: center; font-size: 1.1rem; color: var(--text-light); max-width: 680px; margin: 0 auto 60px;">
  Articles about multi-cloud architecture, platform engineering, SRE patterns, and lessons learned from production systems.
</p>

{% assign latest = site.posts.first %}
{% if latest %}
<div class="post-featured">
  <div class="post-featured-header">
    <span class="post-featured-badge">Latest Post</span>
    <h3><a href="{{ latest.url }}">{{ latest.title }}</a></h3>
    <div class="post-featured-meta">
      <time datetime="{{ latest.date | date_to_xmlschema }}">{{ latest.date | date: "%B %d, %Y" }}</time>
      {% if latest.tags %}
        {% for tag in latest.tags limit:4 %}
          <span class="tag">{{ tag }}</span>
        {% endfor %}
      {% endif %}
    </div>
  </div>
  <div class="post-featured-body">
    <p>{{ latest.excerpt | strip_html | truncatewords: 60 }}</p>
    <a href="{{ latest.url }}" class="btn-primary" aria-label="Read post: {{ latest.title }}">Read post</a>
  </div>
</div>
{% endif %}

{% for post in site.posts offset:1 %}
<div class="post-preview">
  <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>

  <div class="post-meta">
    <time datetime="{{ post.date | date_to_xmlschema }}">
      {{ post.date | date: "%B %d, %Y" }}
    </time>
    {% if post.author %}
      <span>by {{ post.author }}</span>
    {% endif %}
  </div>

  {% if post.tags %}
  <div class="project-tags">
    {% for tag in post.tags %}
      <span class="tag">{{ tag }}</span>
    {% endfor %}
  </div>
  {% endif %}

  <p>{{ post.excerpt | strip_html | truncatewords: 50 }}</p>

  <a href="{{ post.url }}" class="read-more" aria-label="Read more: {{ post.title }}">Read more</a>
</div>
{% endfor %}
