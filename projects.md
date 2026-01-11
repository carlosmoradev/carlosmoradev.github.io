---
layout: page
title: Projects
permalink: /projects/
---

<div class="section-title">
  <h2>Production Projects</h2>
</div>

<p style="text-align: center; font-size: 1.1rem; color: var(--text-light); max-width: 800px; margin: 0 auto 60px;">
  These projects demonstrate multi-cloud platform engineering, data governance, and security automation expertise in production healthcare environments.
</p>

<div class="projects-grid">
{% for project in site.projects %}
  <div class="project-card">
    <div class="project-card-header">
      <h3><a href="{{ project.url }}" style="color: white; text-decoration: none;">{{ project.title }}</a></h3>
      {% if project.tags %}
      <div class="project-tags">
        {% for tag in project.tags limit:4 %}
          <span class="tag" style="background-color: rgba(255,255,255,0.2); color: white; border-color: white;">{{ tag }}</span>
        {% endfor %}
      </div>
      {% endif %}
    </div>
    <div class="project-card-body">
      <p>{{ project.description }}</p>

      {% if project.impact %}
      <div class="project-meta">
        <strong>Impact:</strong> {{ project.impact }}
      </div>
      {% endif %}

      {% if project.tech_stack %}
      <div class="project-meta">
        <strong>Tech Stack:</strong> {{ project.tech_stack }}
      </div>
      {% endif %}

      <a href="{{ project.url }}" class="btn-primary">Read Full Case Study</a>
    </div>
  </div>
{% endfor %}
</div>

{% if site.projects.size == 0 %}
<p style="text-align: center; color: var(--text-light); margin-top: 60px;">
  <em>Project case studies are being added. Check back soon!</em>
</p>
{% endif %}
