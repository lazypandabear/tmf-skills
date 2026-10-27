---
name: tmf-autonomous-networks
description: "TM Forum Autonomous Networks (AN) framework. Use to assess or target network automation levels L0 to L5, design closed-loop operations across resource, service and business layers, apply intent-based management (TMF921), or plan a level evaluation per IG1252."
license: MIT
compatibility: "Agent Skills standard. Works in Hermes Agent and Claude. Knowledge-only; no tools required."
metadata:
  version: 1.0.0
  author: Dennis A. Garcia
  hermes:
    tags: [tmforum, autonomous-networks, zero-touch, closed-loop, intent, ig1252, noc]
    category: tmforum
---

# Autonomous Networks (AN)

## When to Use
- Assess the current automation level of a network domain or workflow.
- Set a target level with a business case.
- Design closed loops, intent interfaces, or human approval gates.

## Core Model
- Six levels, L0 to L5. Load `references/levels.md`.
- Three operational layers: resource operations inside autonomous domains (access, transport, core), service operations across domains, business operations on top. Each layer runs its own closed loop.
- Layers communicate by intent: the upper layer states the outcome; the lower layer decides the method and reports back.
- Key documents: IG1218 business requirements and framework, IG1230 technical architecture, IG1251 reference architecture, IG1252 levels evaluation methodology, IG1253 intent. Intent API: TMF921.
- Load `references/architecture-intent.md` for loop and intent design.

## Procedure: level assessment
1. Scope one autonomous domain and one workflow. Example: access network fault handling.
2. Split the workflow into tasks. Classify each task by cognitive stage: intent or experience, awareness, analysis, decision, execution.
3. For each task, record who performs it: human only, system-assisted, system with human approval, system alone.
4. Score per task. Aggregate per workflow. Report a level per workflow, never one number for the whole network.
5. Pick the next level only where a metric justifies it: MTTR, incidents per 1,000 subscribers, change failure rate, OPEX per site.
6. Define guardrails before raising autonomy: approval gates, rollback, blast-radius limits, audit trail.
7. Check prerequisites: accurate resource and topology inventory (`tmf-sid` Resource domain), clean alarm data (TMF642), API access to domain controllers.

## Reference loading
- Hermes: `skill_view("tmf-autonomous-networks", "references/levels.md")`
- Claude: read `references/levels.md` in this skill's directory.

## Pitfalls
- Network-wide L4 or L5 claims. Levels apply per workflow and domain.
- L5 is a direction, not a near-term target. Most CSPs sit at L1 to L2.
- Automation on dirty inventory. Wrong topology data makes closed loops act on the wrong element.
- "Agentic AI" is a technique, not a level. Score the outcome, not the tool.
- Vendor level scales differ from TM Forum and 3GPP TS 28.100. Normalize before comparing.

## Verification
- Every level claim lists the workflow, domain, task table, and evidence.
- Every target level has a metric, a baseline, and a guardrail.
