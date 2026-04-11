---
layout: post
title: "Your AI workload is not your infrastructure's problem. Until it is."
description: "Infrastructure wasn't designed for AI workloads — and that assumption is now costing teams real money. Four concrete areas Platform Engineers should review before the bill arrives."
date: 2026-04-11
tags: ["platform-engineering", "sre", "ai-agents", "infrastructure", "finops", "llm"]
author: "Carlos Mora"
image: /assets/images/social-card.png
---

There's a conversation happening in the software architecture community about how bad code design inflates LLM token consumption. It's a valid point. But it misses an entire layer of the problem — the one Platform Engineers and SREs actually own.

Most infrastructure running AI workloads today was not designed for them. It was designed to make software artifacts run. That's a different problem, and it has a different cost.

## The infrastructure assumption that breaks under AI

Traditional infrastructure design answers one question: can this artifact deploy and run?

Compute? Sized for average load. Network? Enough bandwidth for expected traffic. Storage? Enough for the data the app needs. Security? Perimeter defined, access controlled.

That model works for deterministic workloads. You know what the artifact needs. You provision for it. You monitor it.

AI workloads break the assumption at the foundation. The resource profile isn't fixed — it shifts with every inference call, every context window, every agent loop iteration. The same infrastructure that handles your morning traffic can behave completely differently at 3pm when a poorly scoped agent starts chaining tool calls.

Nobody sized for that. Because nobody asked the infrastructure question before deploying.

## What "infrastructure readiness for AI" actually means

It's not a checklist. It's a mindset shift: infrastructure is not a deployment target for AI workloads — it's an active variable in their cost, latency, and reliability.

That shift surfaces four concrete areas worth reviewing before — or while — running AI in production.

**1. Context passing architecture**

Every token sent to a model costs money. Where does that context come from, and how is it assembled? In many infrastructures, context is rebuilt from scratch on every request: full conversation history pulled from a database, system instructions fetched from a config store, user data loaded from multiple services — all assembled in the application layer on each call.

The infrastructure question is: where can this be cached, pre-assembled, or compressed without losing fidelity? A well-designed caching layer between your application and your model endpoint can reduce token consumption significantly without touching a single line of application code.

**2. Model routing and gateway configuration**

Most teams deploy AI workloads with a direct application-to-model-endpoint pattern. One app, one model, one endpoint. That works in a pilot. It doesn't scale, and it doesn't optimize.

An AI gateway layer — whether that's a managed service or a self-hosted proxy — enables model routing based on request complexity, cost thresholds, or latency requirements. Simple requests go to cheaper, faster models. Complex reasoning tasks go to the capable but expensive ones. That routing logic lives in infrastructure, not in application code.

If your current infrastructure has no routing layer between your application and your model endpoints, every request is treated the same regardless of what it actually needs.

**3. Retry and timeout configuration**

LLM calls fail. They time out. They return partial responses. The default retry behavior inherited from your existing infrastructure — designed for fast, deterministic API calls — is almost certainly wrong for inference workloads.

Aggressive retries on a timed-out LLM call don't recover the request. They generate duplicate token consumption and compound the latency problem. Infrastructure that wasn't configured with AI call patterns in mind will retry its way into a cost spike before anyone notices.

Reviewing timeout thresholds, retry policies, and circuit breaker configurations for AI-specific endpoints is unglamorous work. It's also directly impactful.

**4. Observability gaps inherited from pre-AI infrastructure**

This one connects to a broader problem. Infrastructure deployed before AI workloads were introduced was instrumented for traditional signals: error rates, latency, throughput. Those signals don't tell you what's happening inside an inference call.

Token consumption, context size per request, model latency versus total request latency, MCP call chains — none of these appear in dashboards built for microservices. If your observability layer wasn't updated when AI workloads were introduced, you're monitoring the infrastructure around the problem, not the problem itself.

## The optimization conversation nobody is having

The original framing — "fix your software architecture to reduce token consumption" — puts the responsibility on the application layer. That's fair. But it leaves Platform Engineers in a passive role: waiting for developers to write better code while watching the inference bill grow.

The infrastructure layer has more leverage than it's given credit for. Caching, routing, retry configuration, and observability are all infrastructure concerns. Optimizing them doesn't require touching application code. It requires treating infrastructure as an active participant in AI workload performance — not just a surface to deploy on.

Most teams haven't had that conversation yet. The ones that do it early will spend significantly less time explaining unexpected cost spikes later.

---

*This post is part of an ongoing series on operating AI systems in production infrastructure. If you found it useful, the post on [AI observability gaps in 2026](/2026/04/03/ai-observability-the-gap-nobody-is-solving/) covers the monitoring side of the same problem.*
