---
layout: page
title: Blog
permalink: /blog/
---

<div class="section-title">
  <h2>Technical Writing</h2>
</div>

<p style="text-align: center; font-size: 1.1rem; color: var(--text-light); max-width: 800px; margin: 0 auto 60px;">
  Articles about multi-cloud architecture, platform engineering, SRE patterns, and lessons learned from production systems.
</p>

{% for post in site.posts %}
<div class="post-preview">
  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>

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

  <a href="{{ post.url }}" class="read-more">Read more</a>
</div>
{% endfor %}
