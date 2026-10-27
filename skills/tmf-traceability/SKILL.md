---
name: tmf-traceability
description: "Cross-framework traceability for TM Forum work. Use when a task spans two or more TMF frameworks: builds the chain from capability and value stream stage to eTOM process, SID entity, functional framework function, Open API, ODA component, and Autonomous Networks closed loop for a use case."
license: MIT
compatibility: "Agent Skills standard. Works in Hermes Agent and Claude. Knowledge-only; no tools required."
metadata:
  version: 1.0.0
  author: Dennis A. Garcia
  hermes:
    tags: [tmforum, traceability, enterprise-architecture, mapping, etom, sid, oda, open-api]
    category: tmforum
---

# TMF Traceability

## When to Use
- Design a use case end to end. Example: new FTTH order, enterprise VPN fault, partner onboarding.
- Build an RFP or architecture document that must link business to systems.
- Check that a solution design is internally consistent.

## The chain
```
Capability (WHAT the business can do)        tmf-business-architecture
  -> Value stream stage (value delivered)    tmf-business-architecture
    -> eTOM process L2/L3 (HOW)              tmf-etom
      -> SID entity (WHAT data)              tmf-sid
        -> Function (WHICH capability of IT) tmf-functional-framework
          -> Open API (HOW systems talk)     tmf-open-apis
            -> ODA component (WHERE it runs) tmf-oda
              -> Closed loop (HOW it self-operates) tmf-autonomous-networks
```

## Procedure
1. State the use case in one sentence: actor, trigger, outcome.
2. Pick the eTOM end-to-end flow from the `tmf-etom` skill's e2e-flows reference.
3. Create one matrix row per eTOM L2 or L3 step. Use `templates/traceability-matrix.md`.
4. Fill columns left to right. Load the owning skill for each column.
5. Apply consistency rules:
   - Each SID entity has one master component.
   - Each API in a row exposes the entity in that row.
   - Each component sits in exactly one ODA functional block.
   - Each row carries a confidence mark: Verified (from official doc), Reference (from these skills), Assumed.
6. List open questions for every Assumed cell.
7. For a worked example, load `references/worked-example-ftth.md`.

## Reference loading
- Hermes: `skill_view("tmf-traceability", "templates/traceability-matrix.md")`
- Claude: read `templates/traceability-matrix.md` in this skill's directory.

## Pitfalls
- Skipping the data column. Most integration defects trace to entity ownership, not APIs.
- One row covering several eTOM processes. Split it.
- Filling every cell to look complete. Mark unknowns Assumed.

## Verification
- No row lacks an eTOM process, a SID entity, and an API.
- Every Assumed cell has an open question.
