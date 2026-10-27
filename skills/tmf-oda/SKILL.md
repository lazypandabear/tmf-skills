---
name: tmf-oda
description: "TM Forum Open Digital Architecture (ODA). Use for BSS/OSS modernization targets: ODA functional blocks, ODA Components (TMFC IDs, exposed and dependent APIs), the ODA Canvas (Kubernetes runtime), component CTK, and legacy-to-ODA migration planning."
license: MIT
compatibility: "Agent Skills standard. Works in Hermes Agent and Claude. Knowledge-only; no tools required."
metadata:
  version: 1.0.0
  author: Dennis A. Garcia
  hermes:
    tags: [tmforum, oda, architecture, components, canvas, kubernetes, modernization]
    category: tmforum
---

# ODA: Open Digital Architecture

## When to Use
- Define a target BSS/OSS architecture.
- Plan migration from monolithic stacks to components.
- Evaluate a vendor's "ODA-ready" claim.

## Core Model
- ODA references eTOM and SID. It does not replace them. It adds a functional architecture, a component model, and a runtime.
- Architecture views: business architecture, information systems architecture (functional architecture plus SID data architecture), implementation architecture (components, Open APIs, Canvas), governance.
- Six functional blocks: Engagement Management, Party Management, Core Commerce Management, Production, Intelligence Management, Decoupling & Integration. Load `references/functional-blocks.md`.
- ODA Component: self-contained, independently deployable. Declares core function (exposed and dependent Open APIs, events), management function, security function. Specified per component ID, e.g. TMFC028 Party Management.
- ODA Canvas: Kubernetes-based runtime. Components deploy as custom resources; Canvas operators wire API exposure, identity, and observability. Load `references/components-canvas.md`.

## Procedure: legacy-to-ODA migration
1. Map current applications to functional blocks. Reuse the heatmap from `tmf-functional-framework`.
2. For each block, select target components from the ODA Component Directory.
3. For each component, list mandatory exposed APIs. Check what the current system exposes today.
4. Build the Decoupling & Integration layer first: API gateway plus event bus. Route existing traffic through it.
5. Replace one component at a time behind the layer (strangler pattern).
6. Order by business value divided by coupling. Start with high value, low coupling. Product catalog is a common first candidate.
7. In procurement, require directory listing and component CTK evidence.
8. Measure: lead time to launch a new offer, integration effort per change, number of point-to-point interfaces removed.

## Reference loading
- Hermes: `skill_view("tmf-oda", "references/functional-blocks.md")`
- Claude: read `references/functional-blocks.md` in this skill's directory.

## Pitfalls
- A monolith with Open APIs bolted on is not an ODA Component. Components must deploy independently and declare dependencies.
- "ODA-compliant" without a directory listing or CTK result is marketing.
- Big-bang replacement. Decouple first, replace second.
- "AI-driven architecture" is not a requirement. Specify the Intelligence Management functions needed instead.
- Canvas custom resource versions evolve. Check the current version in the Canvas repository.

## Verification
- Every target component has a component ID, block, and list of mandatory APIs.
- Every migration step names the decoupling point and rollback path.
