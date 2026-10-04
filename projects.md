---
layout: page
title: Projects
permalink: /projects/
description: "Platform engineering case studies: multi-account data governance, safe-by-default automation, IAM guardrails, and compliance frameworks for regulated multi-cloud environments (AWS and GCP)."
---

<div class="section-title">
  <h1>Architectural Case Studies</h1>
</div>

<p class="section-lead">
  Battle-tested architectures from regulated multi-cloud environments. Proving that deterministic guardrails, automated least-privilege, and FinOps circuit breakers outperform human vigilance under enterprise scale.
</p>

<div class="projects-grid">
{% for project in site.projects %}
  <div class="project-card">
    <div class="project-card-header">
      <h3><a href="{{ project.url }}">{{ project.title }}</a></h3>
      {% if project.tags %}
      <div class="project-tags">
        {% for tag in project.tags limit:4 %}
          <span class="tag">{{ tag }}</span>
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
