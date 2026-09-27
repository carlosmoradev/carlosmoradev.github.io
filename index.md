---
layout: home
title: Home
description: "Carlos Mora: Senior Platform Engineer with 25+ years of experience. Platform architecture, data platform governance, Zero Trust networking, and compliance automation for regulated multi-cloud environments (AWS and GCP)."
---

<section class="hero">
  <h1>Carlos Mora</h1>
  <p class="hero-subtitle">Senior <span>Platform Engineer</span></p>
  <p class="hero-description">
    25+ years designing and operating infrastructure across on-premise data centers, hybrid architectures, and multi-cloud environments. I define platform standards, build deterministic guardrails, and govern data platforms and security across AWS and GCP in regulated healthcare settings.
  </p>
  <div class="hero-cta">
    <a href="/projects" class="btn-primary">View my work</a>
    <a href="/about" class="btn-secondary">About me</a>
  </div>
</section>

{% assign latest = site.posts.first %}
{% if latest %}
<section>
  <header class="section-title">
    <h2>Latest Post</h2>
  </header>

  <article class="post-featured">
    <div class="post-featured-header">
      <span class="post-featured-badge">New</span>
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
  </article>
</section>

---

{% endif %}
<section>
  <header class="section-title">
    <h2>Areas of Expertise</h2>
  </header>
  <div class="specialties">
    <article class="specialty-item">
      <h3>Multi-Cloud Architecture</h3>
      <p>Multi-account strategies, hybrid connectivity, and network isolation across AWS and GCP</p>
    </article>
    <article class="specialty-item">
      <h3>Data Platform Governance</h3>
      <p>Automated RBAC, multi-layer cost controls, and audit trails for multi-account Snowflake and Databricks</p>
    </article>
    <article class="specialty-item">
      <h3>Identity & Compliance</h3>
      <p>Multi-cloud IAM auditing, Zero Trust network access (ZTNA), and HIPAA, SOC2, and HITRUST automation</p>
    </article>
    <article class="specialty-item">
      <h3>Standardized IaC</h3>
      <p>Modular OpenTofu and Terraform architectures, GitHub Actions OIDC federation, and automated validation</p>
    </article>
  </div>
</section>

---

<section>
  <header class="section-title">
    <h2>Featured Projects</h2>
  </header>

  <div class="projects-grid">
    <article class="project-card">
      <header class="project-card-header">
        <h3>Multi-Account Data Warehouse Governance</h3>
        <div class="project-tags">
          <span class="tag">Python</span>
          <span class="tag">Snowflake</span>
          <span class="tag">Multi-Cloud</span>
        </div>
      </header>
      <div class="project-card-body">
        <p>Automated governance framework for multi-account Snowflake environments across AWS and GCP, enforcing RBAC standards, preview-by-default execution, and multi-layer cost controls.</p>
        <div class="project-meta">
          <strong>Impact:</strong> 95% reduction in audit time<br>
          <strong>Tech:</strong> Python, Snowflake, TOML, Multi-Cloud
        </div>
        <a href="/projects/snowflake-governance" class="btn-primary" aria-label="View case study: Multi-Account Data Warehouse Governance">View Case Study</a>
      </div>
    </article>
  </div>
</section>

---

<section>
  <header class="section-title">
    <h2>Recent Writing</h2>
  </header>

  {% if site.posts.size > 0 %}
    {% for post in site.posts limit:3 %}
    <article class="post-preview">
      <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
      <div class="post-meta">
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time>
        {% if post.tags %}
          <div class="project-tags">
            {% for tag in post.tags limit:3 %}
              <span class="tag">{{ tag }}</span>
            {% endfor %}
          </div>
        {% endif %}
      </div>
      <p>{{ post.excerpt | strip_html | truncatewords: 40 }}</p>
      <a href="{{ post.url }}" class="read-more" aria-label="Read more: {{ post.title }}">Read more</a>
    </article>
    {% endfor %}

    <p style="text-align: center; margin-top: 40px;">
      <a href="/blog" class="btn-primary">View All Posts</a>
    </p>
  {% endif %}
</section>

---

<section>
  <header class="section-title">
    <h2>Certifications</h2>
  </header>

  <article class="certifications-box">
    <div class="cert-content">
      <h3 style="margin-top: 0;">Google Cloud Professional Cloud Architect</h3>
      <p><strong>Status:</strong> Certified</p>
      <p>Production experience with Databricks on GCP, multi-cloud VPC design, IAM governance patterns, and data platform infrastructure.</p>
      <p style="margin-top: 15px;">
        <a href="https://www.credly.com/badges/21eb07dc-eebf-439a-b37b-3fd0130ff742" target="_blank" rel="noopener" style="color: var(--primary-color); font-weight: 600;">
          View Credential →
        </a>
      </p>
    </div>
    <div class="cert-badge">
      <img src="/assets/images/gcp-pca-badge.png" alt="Google Cloud Professional Cloud Architect Badge">
    </div>
  </article>

  <article class="certifications-box">
    <div class="cert-content">
      <h3 style="margin-top: 0;">Google Cloud Associate Cloud Engineer</h3>
      <p><strong>Status:</strong> Certified</p>
      <p>Hands-on experience deploying applications, monitoring operations, and managing enterprise solutions on Google Cloud Platform.</p>
      <p style="margin-top: 15px;">
        <a href="https://www.credly.com/badges/973bb37a-19cd-4c47-9c2a-d6307da51bdd" target="_blank" rel="noopener" style="color: var(--primary-color); font-weight: 600;">
          View Credential →
        </a>
      </p>
    </div>
    <div class="cert-badge">
      <img src="/assets/images/gcp-cea-badge.png" alt="Google Cloud Associate Cloud Engineer Badge">
    </div>
  </article>

  <article class="certifications-box">
    <div class="cert-content">
      <h3 style="margin-top: 0;">AWS Solutions Architect Professional</h3>
      <p><strong>Status:</strong> In Preparation</p>
      <p>Production experience with multi-account architectures, hybrid cloud network connectivity and isolation, IAM security automation, and multi-layer cost controls across AWS and GCP.</p>
    </div>
  </article>
</section>

---

<section>
  <header class="section-title">
    <h2>Get in Touch</h2>
  </header>

  <p style="text-align: center; font-size: 1.1rem; color: var(--text-light); margin-bottom: 30px;">
    Interested in platform architecture, data governance, or multi-cloud security? Let's connect.
  </p>

  <nav style="display: flex; justify-content: center; gap: 20px; flex-wrap: wrap;">
    <a href="https://github.com/{{ site.author.github }}" class="btn-primary" target="_blank" rel="noopener">GitHub</a>
    <a href="https://linkedin.com/in/{{ site.author.linkedin }}" class="btn-primary" target="_blank" rel="noopener">LinkedIn</a>
    <a href="mailto:{{ site.author.email }}" class="btn-primary">Email</a>
  </nav>
</section>
