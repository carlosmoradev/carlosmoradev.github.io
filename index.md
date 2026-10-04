---
layout: home
title: Home
description: "Carlos Mora: Principal Platform Architect & AI Systems Engineer. Multi-cloud architecture, data platform governance, Zero Trust systems, and deterministic AI infrastructure."
---

<section class="hero">
  <h1>Carlos Mora</h1>
  <p class="hero-subtitle">Principal Platform Architect &amp; AI Systems Engineer</p>
  <p class="hero-description">
    If production reliability or compliance depends on human vigilance, the architecture has already failed. With 25+ years designing enterprise infrastructure across on-premise, AWS, and GCP, I build platforms with deterministic guardrails—removing traps from the floor so engineering teams can scale data platforms and AI workloads safely by default.
  </p>
  <nav class="hero-nav" aria-label="Quick navigation">
    <a href="/blog">Essays</a>
    <span class="sep">·</span>
    <a href="/projects">Case Studies</a>
    <span class="sep">·</span>
    <a href="/about">About</a>
    <span class="sep">·</span>
    <a href="https://github.com/{{ site.author.github }}" target="_blank" rel="noopener">GitHub</a>
    <span class="sep">·</span>
    <a href="https://linkedin.com/in/{{ site.author.linkedin }}" target="_blank" rel="noopener">LinkedIn</a>
  </nav>
</section>

{% assign latest = site.posts.first %}
{% if latest %}
<section class="home-section">
  <div class="section-title">
    <h2>Featured Architectural Essay</h2>
  </div>

  <article class="post-featured">
    <div class="post-featured-header">
      <span class="post-featured-badge">Featured Essay</span>
      <h3><a href="{{ latest.url }}">{{ latest.title }}</a></h3>
      <div class="post-featured-meta">
        <time datetime="{{ latest.date | date_to_xmlschema }}">{{ latest.date | date: "%B %d, %Y" }}</time>
        {% if latest.tags %}
          <span class="tag-divider">·</span>
          {% for tag in latest.tags limit:4 %}
            <span class="tag">{{ tag }}</span>
          {% endfor %}
        {% endif %}
      </div>
    </div>
    <div class="post-featured-body">
      <p>{{ latest.excerpt | strip_html | truncatewords: 55 }}</p>
      <a href="{{ latest.url }}" class="read-more" aria-label="Read essay: {{ latest.title }}">Read Essay</a>
    </div>
  </article>
</section>
{% endif %}

<section class="home-section">
  <div class="section-title">
    <h2>Recent Writing</h2>
  </div>

  <div class="posts-list">
    {% for post in site.posts limit:5 %}
    <article class="post-row">
      <div class="post-row-meta">
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%b %d, %Y" }}</time>
      </div>
      <div class="post-row-content">
        <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
        <p>{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
        {% if post.tags %}
        <div class="post-tags">
          {% for tag in post.tags limit:3 %}
            <span class="tag">{{ tag }}</span>
          {% endfor %}
        </div>
        {% endif %}
      </div>
    </article>
    {% endfor %}
  </div>

  <div class="section-footer">
    <a href="/blog" class="read-more">View complete writing archive</a>
  </div>
</section>

<section class="home-section">
  <div class="section-title">
    <h2>Architectural Case Studies</h2>
  </div>

  <div class="projects-container">
    {% for project in site.projects %}
    <article class="project-card">
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
        <a href="{{ project.url }}" class="read-more">Read Retrospective</a>
      </div>
    </article>
    {% endfor %}
  </div>
</section>

<section class="home-section">
  <div class="section-title">
    <h2>Architectural Convictions</h2>
  </div>

  <div class="convictions-list">
    <article class="conviction-item">
      <h3>Deterministic Guardrails over Human Vigilance</h3>
      <p>A Slack message, a post-deploy checklist, or a "be careful" warning is an architectural antipattern. If an engineer can trigger an outage by missing a notification on a Friday afternoon, the failure belongs to the platform design. Structural IAM constraints and automated pre-flight gates prevent errors before execution.</p>
    </article>
    <article class="conviction-item">
      <h3>Zero Trust for Autonomous &amp; Agentic Workloads</h3>
      <p>Exposing APIs to LLMs without ephemeral credentials, identity federation, and execution gateways turns agentic tooling into arbitrary remote code execution. AI agents must operate under the same least-privilege boundaries and audit trails as human operators.</p>
    </article>
    <article class="conviction-item">
      <h3>Multi-Layer Cost Circuit Breakers</h3>
      <p>Cost control in distributed data platforms cannot rely on end-of-month invoice reconciliations. FinOps discipline requires proactive architectural circuit breakers: strict warehouse auto-suspend policies, statement timeouts, resource monitors, and query connection reuse embedded into IaC.</p>
    </article>
    <article class="conviction-item">
      <h3>Compliance by Construction</h3>
      <p>In regulated enterprise environments (HIPAA, SOC 2, HITRUST), compliance cannot be a panicked quarterly audit scramble. It must be an immutable, continuously generated byproduct of platform automation, OIDC federation, and immutable change logs.</p>
    </article>
  </div>
</section>
