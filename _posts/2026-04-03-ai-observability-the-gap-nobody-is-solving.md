---
layout: post
title: "AI Observability: the problem nobody is solving well in 2026"
description: "Monitoring hallucinations, prompt drift, MCP call latency, and inference costs in production is the new frontier of modern SRE. And almost nobody has a complete stack for it."
date: 2026-04-03
tags: ["sre", "observability", "ai-agents", "platform-engineering", "opentelemetry"]
author: "Carlos Mora"
image: /assets/images/social-card.png
---

We've spent years building AIOps — using AI to observe infrastructure. But there's a more urgent problem taking shape: who observes the AI itself?

Monitoring hallucinations, prompt drift, MCP call latency, and inference costs in production is the new frontier of modern SRE. And almost nobody has a complete stack for it.

## The monitoring gap is structural, not tactical

Your current observability stack was built for deterministic systems. A service either returns 200 or it doesn't. Latency is measurable. Error rates are countable. SLOs make sense because "correct behavior" is definable.

AI systems break all of these assumptions.

The failure mode isn't a 500 error — it's a confident hallucination delivered with perfect latency and a 200 status code. Your dashboards are green. Your AI is producing garbage. A Fortune 100 bank misrouted 18% of critical cases without triggering a single alert.

This isn't a tooling gap you can close by adding a plugin to your existing stack. It's a paradigm problem.

## The current landscape: 15+ tools, zero consensus

The AI observability market hit $510M in 2024, growing at 32% annually. That sounds like a mature space. It isn't.

The landscape splits into two camps that don't talk to each other:

**AI-native platforms** (Langfuse, LangSmith, Arize Phoenix, Helicone, Braintrust) understand prompts, tokens, and semantic evaluation — but have no context about your infrastructure, your SLOs, or your cost centers.

**Traditional APM vendors** (Datadog, New Relic, Dynatrace, Grafana) understand infrastructure deeply — but treat AI as just another microservice, missing everything that makes AI systems different.

OpenTelemetry's GenAI Semantic Conventions are the closest thing to a unifying standard — still experimental as of Q1 2026, not GA. Every major vendor has adopted them as a wire format while building proprietary analytics on top. The instrumentation layer is converging. Everything above it is fragmented.

## Four gaps practitioners can't close

**1. Inference cost is invisible at the decision layer**

AI inference cost is generated where routing decisions happen — model selection, retry logic, token budgets, context window management. Your observability monitors the infrastructure layer. These are different layers, and the gap between them is expensive.

A typical pattern: a poorly optimized prompt costs more per day than the entire Kubernetes cluster running the application. One team discovered they were paying an LLM to be reminded of its job — sending the same system instructions hundreds of times daily. Reasoning models like o3 add internal "thinking tokens" that inflate consumption silently. Output tokens cost 3–10x more than input tokens.

What looks like $500/month in a pilot becomes $15,000 at production scale. Before accounting for growth.

**2. MCP traces break at the boundary**

97 million monthly SDK downloads. 5,800+ MCP servers in the ecosystem. And a fundamental tracing problem: when a user request flows from Agent → LLM Provider → MCP Server → External Tool, the trace breaks at the MCP boundary. Two disconnected traces. No correlation. No end-to-end visibility.

Sentry shipped the first dedicated MCP monitoring tool in mid-2025 — after running their own MCP server at 50 million requests per month and discovering random user timeouts with no results and no errors. No way to even know how many users were affected.

OpenTelemetry's MCP semantic conventions remain in draft.

**3. Silent semantic failures don't trigger alerts**

A single user request can trigger 15+ LLM calls across embedding generation, vector retrieval, context assembly, reasoning steps, and response synthesis. Every traditional metric can look healthy while the output is meaningless.

44% of organizations still rely on manual methods to monitor AI agent interactions. The current state-of-the-art for detecting semantic failures in production is largely "a human reads logs and guesses." Most teams discover problems through downstream business metrics — weeks after the damage.

**4. SLOs don't exist for non-deterministic systems**

This is the open question practitioners keep returning to. Traditional SRE practice assumes you can define expected behavior, measure deviation, and set error budgets. When the same input can legitimately produce different outputs, when "correct" requires semantic judgment, and when model providers silently update weights underneath you — the entire SLI/SLO framework needs rethinking.

Nobody has solved this. The conversation is still at the "how do we even frame the problem" stage.

## The cost paradox

Adding AI monitoring to Datadog increases observability bills by 40–200%. A typical RAG pipeline generates 10–50x more telemetry than an equivalent API call. LangSmith customers routinely sample down to 0.1% of production traffic to control costs.

You end up paying significantly more to observe significantly less.

Gartner predicts that more than 40% of agentic AI projects will be canceled by 2027. The Dynatrace 2026 Pulse of Agentic AI survey found that 51% of engineering leaders cite limited visibility into agent behavior as their top technical blocker.

## What's actually converging

OpenTelemetry is winning the instrumentation war. The GenAI SIG has defined semantic conventions for LLM spans, agent spans, tool execution, token metrics, and evaluation events. Every major vendor accepts OTel GenAI spans.

That's the one genuine convergence story. Everything above the wire format remains fragmented — comparable to cloud monitoring circa 2010–2012. Except OpenTelemetry's existence may accelerate consolidation faster than it happened last time.

## The practitioner reality

This is the infrastructure monitoring crisis of 2010 all over again. The stakes are higher. The systems are non-deterministic. The failure modes are semantic rather than structural.

If you're an SRE or Platform Engineer who's been handed responsibility for AI systems without the tools to properly operate them — that's the actual state of the industry, not a gap in your skills or your team's preparation.

The tooling will converge. OpenTelemetry will help. The ecosystem is moving.

But right now, in early 2026, most teams are flying partially blind — and the first step is naming the problem clearly enough to start solving it.

---

*Data points: Dynatrace 2026 Pulse of Agentic AI (919 leaders), KubeCon Atlanta 2025, OneUptime AI Observability Cost Analysis, Sentry MCP Server Monitoring launch, Gartner 2025–2027 predictions, Pydantic AI observability pricing analysis.*
