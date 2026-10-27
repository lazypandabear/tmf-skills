---
name: tmf-etom
description: "TM Forum Business Process Framework (eTOM, GB921). Use to classify, decompose, or map telecom business processes: SIP vs Operations vs Enterprise Management, Fulfillment, Assurance, Billing, process levels L0 to L3, domain groupings, end-to-end flows."
license: MIT
compatibility: "Agent Skills standard. Works in Hermes Agent and Claude. Knowledge-only; no tools required."
metadata:
  version: 1.0.0
  author: Dennis A. Garcia
  hermes:
    tags: [tmforum, etom, gb921, business-process, bss, oss]
    category: tmforum
---

# eTOM: Business Process Framework (GB921)

## When to Use
- Map a CSP's as-is or to-be processes to the industry reference.
- Locate a process. Example: "Where does number porting or fault repair sit?"
- Define process scope for an RFP, a KPI set, or a transformation program.

## Core Model
- Level 0 areas: Strategy, Infrastructure & Product (SIP). Operations (OPS). Enterprise Management.
- Vertical groupings. End-to-end. The executive view.
  - SIP: Strategy & Commit. Infrastructure Lifecycle Management. Product Lifecycle Management.
  - OPS: Operations Support & Readiness. Fulfillment. Assurance. Billing & Revenue Management.
- Horizontal groupings. Functional domains: Market/Sales, Product, Customer, Service, Resource, Supplier/Partner (Business Partner in newer releases), Enterprise.
- Current releases use the domains as the primary categorization, crossed with SIP and OPS.
- Levels: L0 areas. L1 groupings. L2 core processes. L3 tasks and flows. L4 and below are operator-specific.

## Procedure
1. Phase: planning or building (SIP), running (OPS), or corporate (Enterprise Management).
2. Domain: which object the process acts on. Customer, service, resource, partner, product, market.
3. Vertical (OPS only): Fulfillment, Assurance, Billing, or Support & Readiness.
4. The intersection gives the L1 grouping. Load `references/domains.md` for L2 names.
5. For cross-domain journeys, load `references/e2e-flows.md`.
6. For the full L0/L1 tree, load `references/structure.md`.
7. Stop at L3 for reference mapping. Mark L4 and below as operator-specific.
8. Hand data objects to `tmf-sid`. Hand functions to `tmf-functional-framework`.

## Reference loading
- Hermes: `skill_view("tmf-etom", "references/domains.md")`
- Claude: read `references/domains.md` in this skill's directory.

## Pitfalls
- FAB are vertical end-to-end groupings, not horizontal layers. Many summaries invert this. Correct it.
- eTOM classifies processes. It is not a workflow engine and not an org chart. Do not build departments 1:1 from L1 boxes.
- Naming a process with eTOM labels is not conformance. Conformance requires a TM Forum assessment.
- L2 and L3 names change between releases. Always state the release used.

## Verification
- Each mapped process states: L0 area, domain, vertical, level, release.
- No process maps to two domains without a written reason.
