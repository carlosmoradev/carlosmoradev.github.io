---
layout: home
title: Home
---

<section class="hero">
  <h1>Carlos Mora</h1>
  <h2>I'm a <span>Platform Engineer & Site Reliability Engineer</span></h2>
  <p class="hero-description">
    I build multi-cloud infrastructure that scales and automate the complex: from managing multi-account Snowflake environments across AWS and GCP to connecting clouds with Zero Trust networks. Specialized in making the complicated simple and the manual automatic.
  </p>
</section>

<section class="specialties">
  <article class="specialty-item">
    <strong>Multi-Cloud Infrastructure</strong>
    <p>AWS & GCP in production environments with multi-account strategies and hybrid connectivity patterns</p>
  </article>
  <article class="specialty-item">
    <strong>Data Platform Governance</strong>
    <p>Snowflake, Databricks automation with RBAC, cost controls, and compliance built-in</p>
  </article>
  <article class="specialty-item">
    <strong>Security & Compliance</strong>
    <p>Multi-cloud IAM auditing, HIPAA/SOC2/HITRUST automation, and Zero Trust implementations</p>
  </article>
  <article class="specialty-item">
    <strong>Infrastructure as Code</strong>
    <p>OpenTofu/Terraform at scale with reusable modules, GitHub Actions OIDC, and validation frameworks</p>
  </article>
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
        <p>Automated governance for multi-account Snowflake environments across AWS and GCP. Python framework with multi-layer cost controls and RBAC automation.</p>
        <div class="project-meta">
          <strong>Impact:</strong> 95% reduction in audit time<br>
          <strong>Tech:</strong> Python, Snowflake, Pandas, Multi-cloud
        </div>
        <a href="/projects/snowflake-governance" class="btn-primary">View Case Study</a>
      </div>
    </article>

    <article class="project-card">
      <header class="project-card-header">
        <h3>Zero Trust Network Automation</h3>
        <div class="project-tags">
          <span class="tag">OpenTofu</span>
          <span class="tag">AWS</span>
          <span class="tag">GCP</span>
        </div>
      </header>
      <div class="project-card-body">
        <p>Multi-cloud VPN automation with OpenTofu. 5 reusable modules for AWS and GCP connector deployment with intelligent DNS management.</p>
        <div class="project-meta">
          <strong>Impact:</strong> 80% reduction in deployment time<br>
          <strong>Tech:</strong> OpenTofu, CloudConnexa, GitHub Actions
        </div>
        <a href="/projects#zero-trust" class="btn-primary">Coming Soon</a>
      </div>
    </article>

    <article class="project-card">
      <header class="project-card-header">
        <h3>Multi-Cloud IAM Audit Tool</h3>
        <div class="project-tags">
          <span class="tag">Python</span>
          <span class="tag">Security</span>
          <span class="tag">Compliance</span>
        </div>
      </header>
      <div class="project-card-body">
        <p>Production security tool for auditing IAM permissions across AWS and GCP with risk-based categorization for compliance reporting.</p>
        <div class="project-meta">
          <strong>Impact:</strong> 70% reduction in security audit time<br>
          <strong>Tech:</strong> Python, boto3, gcloud CLI
        </div>
        <a href="/projects#iam-audit" class="btn-primary">Coming Soon</a>
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
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
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
      <a href="{{ post.url }}" class="read-more">Read more</a>
    </article>
    {% endfor %}

    <p style="text-align: center; margin-top: 40px;">
      <a href="/blog" class="btn-primary">View All Posts</a>
    </p>
  {% else %}
    <p style="text-align: center; color: var(--text-light);">
      <em>Blog posts coming soon! Check back later for technical articles on multi-cloud architecture and platform engineering.</em>
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
      <h3 style="margin-top: 0;">✅ Google Cloud Professional Cloud Architect</h3>
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
      <h3 style="margin-top: 0;">✅ Google Cloud Associate Cloud Engineer</h3>
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
      <h3 style="margin-top: 0;">🎯 AWS Solutions Architect Professional</h3>
      <p><strong>Status:</strong> In Preparation</p>
      <p>Hands-on production experience with multi-account architectures, hybrid cloud connectivity (RDS Proxy + NLB), IAM security automation, and cost optimization strategies across AWS and GCP.</p>
    </div>
  </article>
</section>

---

<section>
  <header class="section-title">
    <h2>Get in Touch</h2>
  </header>

  <p style="text-align: center; font-size: 1.1rem; color: var(--text-light); margin-bottom: 30px;">
    Interested in multi-cloud architecture, platform engineering, or SRE practices? Let's connect!
  </p>

  <nav style="display: flex; justify-content: center; gap: 20px; flex-wrap: wrap;">
    <a href="https://github.com/{{ site.author.github }}" class="btn-primary" target="_blank" rel="noopener">GitHub</a>
    <a href="https://linkedin.com/in/{{ site.author.linkedin }}" class="btn-primary" target="_blank" rel="noopener">LinkedIn</a>
    <a href="mailto:{{ site.author.email }}" class="btn-primary">Email</a>
  </nav>
</section>
