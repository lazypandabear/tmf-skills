---
name: tmf-business-architecture
description: "TM Forum Business Architecture: Capability Framework (TMF-CF, GB1029C Capability Map) and Value Stream Framework (TMF-VSF, GB1029V). Use for capability maps and heatmaps, portfolio and investment planning, value stream modelling, and linking strategy to eTOM processes and ODA components."
license: MIT
compatibility: "Agent Skills standard. Works in Hermes Agent and Claude. Knowledge-only; no tools required."
metadata:
  version: 1.0.0
  author: Dennis A. Garcia
  hermes:
    tags: [tmforum, capability-map, value-stream, business-architecture, archimate, portfolio]
    category: tmforum
---

# Business Architecture: Capabilities and Value Streams

## When to Use
- Build or score a capability map for a CSP or business unit.
- Decide where to invest in a transformation portfolio.
- Model how value reaches a stakeholder, stage by stage.

## Core Model
- Capability: an ability an organization, person, or system possesses, focused on outcomes. Answers WHAT the business can do. Realized by people, processes, information, and systems.
- Value stream: stakeholder-initiated sequence of value-adding stages. Each stage adds incremental value. Realized by business processes.
- Both use ArchiMate 3.2 concepts.
- Value stream principles: outcome focus, reusability across products, flow adaptability (skip, repeat, or end stages early).
- Maturity: Capability Map GB1029C is Beta (v3.0.x, 2025). Value Stream Framework GB1029V is early-stage (v1.0.4, 2024). Treat both as evolving.

## Procedure: capability heatmap
1. Take the capability map to Level 2. Load `references/capability-map.md`.
2. Score each capability: current maturity 1 to 5, strategic importance 1 to 5. Record evidence per score.
3. Priority = importance minus maturity. Rank descending.
4. For each top capability, list realizing elements: eTOM processes (`tmf-etom`), SID entities (`tmf-sid`), functions and ODA components (`tmf-functional-framework`, `tmf-oda`).
5. Output an investment backlog: capability, gap, initiative, cost band, KPI.

## Procedure: value stream
1. Name the stakeholder and the trigger.
2. Define 4 to 8 stages. Each stage: entrance criteria, exit criteria, value item.
3. Attach enabling capabilities and realizing eTOM processes per stage.
4. Load `references/value-streams.md` for the template.

## Reference loading
- Hermes: `skill_view("tmf-business-architecture", "references/value-streams.md")`
- Claude: read `references/value-streams.md` in this skill's directory.

## Pitfalls
- Capability is not process. Capability says what; process says how. "Order Handling" is a process; "Order Management" is a capability.
- Capability maps that mirror the org chart. Capabilities stay stable when the organization changes.
- Scoring without evidence. Every maturity score needs a data point.
- Inventing TM Forum capability IDs. Use names; cite GB1029C for official structure.

## Verification
- Every scored capability has evidence and an owner.
- Every value stream stage links to at least one capability and one eTOM process.
