---
layout: post
title: "From ticket to PR with agents: how to use Claude to automate platform changes without breaking SLOs"
description: "AI agents in platform engineering aren't about generating code — they're about closing the loop between operational intent and reviewable execution. Here's how the pattern works and why the pull request is the key unit of governance."
date: 2026-03-27
tags: ["platform-engineering", "sre", "ai-agents", "claude", "automation"]
author: "Carlos Mora"
image: /assets/images/social-card.png
---

In Platform Engineering and SRE, the hardest part of change is rarely writing the change itself. The hard part is everything around it: understanding the intent behind a ticket or incident, locating the right context, identifying the systems involved, deciding what should change, validating the blast radius, documenting rollback, and making the result legible enough for someone else to review with confidence.

That is why I think the real promise of Claude is not code generation. It is the ability to help close the loop between operational intent and reviewable execution.

## The translation problem

A ticket, incident, or operational task expresses intent. But between that intent and a merged change, there is usually a long chain of manual translation. Engineers need to gather context from runbooks, infrastructure repositories, dashboards, previous incidents, documentation, and platform conventions. They need to decide whether the task requires a configuration tweak, an IaC change, a runbook update, or some combination of all three. They need to make the work explicit enough to review and safe enough to deploy.

That translation layer is where Claude becomes interesting.

Anthropic describes effective agents as systems that use tools dynamically, adapt based on feedback from the environment, and operate with clear stopping conditions and human oversight. That is a much more useful framing than treating Claude as a smarter autocomplete layer.

## The pattern

Applied to Platform Engineering, the workflow looks something like this:

1. A ticket, incident, or task becomes the initial statement of intent.
2. Claude gathers context from the relevant repos, documentation, and operational systems.
3. It uses tools to inspect files, compare configurations, reason about likely changes, and validate assumptions.
4. It produces a proposed change in a form that the team can actually govern — ideally as a pull request.
5. Humans review the result, enforce policy, and decide whether it should ship.

## The pull request as the unit of governance

The pull request is the key unit here.

The real output of an agent in this workflow should not be a blob of generated code. It should be a reviewable change set with rationale, scope, validation steps, and rollback guidance. Once the output becomes a PR rather than a prompt response, the conversation shifts from "Can the model write this?" to "Can the organization safely absorb and govern this change?"

That distinction matters because SRE is not optimized for novelty. It is optimized for reliability. A change that is fast but opaque is often worse than a change that is slower but auditable. If Claude is going to be useful in platform workflows, it has to increase clarity, not just speed.

## Why SLOs matter in the title

This is also why the phrase "without breaking SLOs" matters so much. It prevents the conversation from drifting into generic AI optimism. In a platform context, any serious use of agents has to be evaluated against reliability outcomes. Faster workflows are not automatically better workflows if they increase incident risk, reduce operator understanding, or blur accountability.

## Guardrails are not obstacles — they are the design

A credible workflow therefore needs guardrails. At minimum, that means:

- Clear tool boundaries and scoped permissions
- Strong context about the system being changed
- Validation before merge
- Human review for sensitive or high-impact changes
- Explicit rollback paths
- Traceability from original intent to final diff

This guardrail-heavy framing is not anti-agent. It is what makes agents useful in production environments. Anthropic's own materials emphasize that agents work best when they can interact with the environment, test their assumptions, and operate inside structured limits rather than open-ended autonomy.

## The real opportunity

That is why I think the most interesting future for Claude in Platform Engineering is not "AI writes infrastructure code." It is "AI helps translate operational work into changes that humans can evaluate, approve, and ship with confidence."

Seen this way, Claude is not just a writing assistant or coding assistant. It starts to look more like an operational interface — a system that sits between intent and execution, helping teams move from ticket to PR with more context, better traceability, and less manual translation overhead.

Not replacing engineers.

Not removing judgment.

But reducing the distance between work that needs to happen and changes that are safe enough to review, govern, and deploy.
