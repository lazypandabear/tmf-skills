---
name: tmf-functional-framework
description: "TM Forum Functional Framework, formerly Application Framework or TAM (GB929). Use to classify BSS/OSS applications and functions, run application rationalization, map vendor capabilities, or define RFP functional scope. Links functions to eTOM processes and SID entities."
license: MIT
compatibility: "Agent Skills standard. Works in Hermes Agent and Claude. Knowledge-only; no tools required."
metadata:
  version: 1.0.0
  author: Dennis A. Garcia
  hermes:
    tags: [tmforum, tam, gb929, application-map, functional-framework, rationalization]
    category: tmforum
---

# Functional Framework / TAM (GB929)

## When to Use
- Application portfolio rationalization. Find overlaps and gaps.
- Map a vendor product to standard functions.
- Write the functional scope of an RFP without naming products.

## Core Model
- TAM began as a map of telecom application areas.
- It evolved into a normalized functional decomposition (GB929F). Reason: CSP application boundaries rarely match the TAM application list, but the functions inside them hold.
- Domains align with eTOM and SID domains. Each application area maps to SID L1 ABEs and eTOM L2 processes.
- Current suite: GB929 v25.0 (July 2025). Verify before citing.

## Procedure: application rationalization
1. List current applications: name, vendor, version, modules, owner.
2. Decompose each application into functions. Map functions, not applications. Load `references/domains.md`.
3. Build a heatmap: function rows, application columns.
4. Flag overlap: two or more applications perform one function.
5. Flag gaps: zero applications perform a required function.
6. Link each function to the eTOM L2 it supports (`tmf-etom`) and the SID ABE it masters (`tmf-sid`).
7. Assign exactly one system of record per SID ABE.
8. Output consolidation and decommission candidates with cost, risk, and dependency notes.

## Procedure: RFP functional scope
1. List required functions by domain.
2. For each function, list required Open APIs exposed and consumed (`tmf-open-apis`).
3. Request vendor evidence per function: demo, API conformance report, reference customer.

## Reference loading
- Hermes: `skill_view("tmf-functional-framework", "references/domains.md")`
- Claude: read `references/domains.md` in this skill's directory.

## Pitfalls
- Mapping vendor modules 1:1 to TAM application boxes. Map functions.
- Two systems mastering one entity (customer, product catalog). Root cause of most data quality failures.
- Using TAM as the target architecture. Use ODA functional blocks for the target (`tmf-oda`).
- Vendor "TAM coverage" percentages are self-reported. Treat as unverified.

## Verification
- Every function cell links to one eTOM L2 and one SID ABE.
- Every SID ABE has exactly one system of record.
