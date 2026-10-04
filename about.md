---
layout: page
title: About
permalink: /about/
description: "Platform Architect with 25+ years of experience across multi-cloud environments. Defining platform standards, data platform governance, IAM automation, and compliance guardrails on AWS and GCP."
---

<div class="section-title">
  <h1>About Me</h1>
</div>

I am Carlos Mora, a Platform Architect with 25+ years of experience spanning on-premise data centers, hybrid architectures, and multi-cloud platforms. I define platform standards, build deterministic guardrails, and govern data platforms and security in regulated enterprise environments.

Throughout my career, I have designed multi-account Snowflake governance frameworks, automated Zero Trust network architectures connecting AWS and GCP, and built least-privilege IAM automation for regulated compliance.

## Core Principles

- **Deterministic guardrails over human vigilance:** Automate compliance, permissions, and cost controls so that safe, reliable operations are the default path.
- **Documentation as the single source of truth:** Maintain clear architectural decision records and runbooks that allow any engineer to operate and extend platforms safely.
- **Platforms others can use safely:** Design abstractions and tooling that internal engineering teams can adopt without needing specialized cloud administration expertise.
- **Security and compliance by design:** Embed least privilege, auditability, and graceful degradation into the architecture from day one rather than retrofitting them before audits.

## Capability Domains

### Multi-Account Data Platform Governance
Establishing centralized access controls, automated role management, and multi-layer cost controls across distributed data platforms.
- Multi-account Snowflake RBAC automation and permission risk categorization
- Databricks Unity Catalog on GCP
- Multi-layer cost defense (warehouse policies, resource monitors, and connection reuse)
- Cross-account change detection with graceful degradation

### Secure Connectivity & Data Access
Designing network isolation and controlled data access across AWS and GCP for sensitive workloads.
- Zero Trust Network Access (ZTNA) and hybrid multi-cloud connectivity
- Secure database access layers with connection pooling
- VPN connectivity automation across multiple VPCs

### Identity, Access & Compliance Governance
Translating regulatory requirements (HIPAA, SOC2, HITRUST) into automated platform controls and verifiable audit trails.
- Multi-cloud IAM auditing and automated permission risk categorization
- GitHub Actions OIDC federation (zero long-lived credentials in CI/CD)
- Credential rotation without downtime
- Automated compliance reporting and audit readiness

### Standardized Infrastructure as Code
Building reusable, tested, and documented IaC module libraries that enforce architectural guardrails across teams.
- Multi-cloud OpenTofu and Terraform module libraries
- Validation and pre-deployment checks
- State management and backend configuration standards

### AI Platform Security & Governance (Current Focus)
Applying platform engineering discipline and Zero Trust security principles to agentic workflows and AI integrations.
- Zero Trust boundaries and least-privilege constraints for Model Context Protocol (MCP) integrations
- Operational observability patterns for non-deterministic AI workloads
- Agent-assisted engineering workflows with deterministic guardrails and pull-request verification

## Technical Stack Summary

- **Cloud:** AWS and GCP (multi-account)
- **Data Platforms:** Snowflake, Databricks, BigQuery
- **Infrastructure as Code:** OpenTofu, Terraform, GitHub Actions
- **Languages:** Python, TypeScript/Node.js
- **Compliance:** HIPAA, SOC2, HITRUST

## Current Focus

- **Certifications:** [Google Cloud Professional Cloud Architect](https://www.credly.com/badges/21eb07dc-eebf-439a-b37b-3fd0130ff742) (Certified), [Google Cloud Associate Cloud Engineer](https://www.credly.com/badges/973bb37a-19cd-4c47-9c2a-d6307da51bdd) (Certified), preparing for AWS Solutions Architect Professional.
- **Writing:** Documenting platform governance, FinOps lifecycle management, and practical Zero Trust architecture on [carlosmora.dev/blog](/blog).
- **Open Source:** Developing platform tooling, agentic workflow extensions, and reusable architecture patterns for the engineering community.

## Platform Engineering at Regulated Scale

Operating platforms in regulated environments requires systems designed for auditability, resilience, and strict access boundaries:

- **Regulated multi-cloud scale:** Multi-account data warehouse governance and OpenTofu/Terraform module libraries across AWS and GCP.
- **Safe-by-default tooling:** Administrative tooling executes in preview mode by default. Destructive or privileged modifications require explicit elevation, preventing unintended changes.
- **Compliance by design:** Automated change detection, least-privilege RBAC, and multi-layer cost controls embedded directly into platform infrastructure.
- **Resilience through graceful degradation:** Administrative and audit pipelines tolerate single-account maintenance or transient network partitions without halting broader governance sweeps.
- **Operational documentation:** Two-layer documentation discipline combining clear operator runbooks for engineering teams with structured architectural decision records.

## Beyond Code

After 25+ years in infrastructure, spanning on-premise data centers to multi-cloud at scale, I have learned that sustainable performance engineering applies to systems AND people.

As a neurodivergent engineer, I approach complex systems with pattern recognition that is both a strength and a responsibility. The same principles that prevent infrastructure burnout (observability, graceful degradation, capacity planning) apply to career sustainability.

The tech industry often celebrates "hustle culture" and endless availability. I have learned that the engineers who last decades (and who ship reliable systems consistently) treat their own capacity as seriously as they treat system capacity. Monitoring your own metrics matters as much as monitoring your infrastructure.

I occasionally write about burnout prevention, neurodivergence in tech, and building careers that last decades, not just sprints.

---

Want to connect? Find me on [GitHub](https://github.com/carlosmoradev), [LinkedIn](https://linkedin.com/in/carlosmoradev), or [email](mailto:hi@carlosmora.dev).
