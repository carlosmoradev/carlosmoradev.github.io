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

{% if site.posts.size == 0 %}
<div style="text-align: center; padding: 80px 20px; background: var(--bg-light); border-radius: 10px;">
  <h3 style="color: var(--secondary-color); margin-bottom: 20px;">Blog Coming Soon</h3>
  <p style="color: var(--text-light); font-size: 1.1rem; max-width: 600px; margin: 0 auto;">
    Technical articles on multi-cloud architecture and platform engineering are in the works. Check back soon or connect with me to stay updated!
  </p>
  <div style="margin-top: 30px;">
    <a href="/" class="btn-primary">Return Home</a>
  </div>
</div>
{% endif %}
