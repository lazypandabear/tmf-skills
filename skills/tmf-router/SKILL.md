---
name: tmf-router
description: "Entry point for any TM Forum (TMF) question. Classifies the request and routes to the right TMF skill: eTOM, SID, Functional Framework (TAM), Open APIs, ODA, Autonomous Networks, Capability and Value Stream, traceability, or architecture review."
license: MIT
compatibility: "Agent Skills standard. Works in Hermes Agent and Claude. Knowledge-only; no tools required."
metadata:
  version: 1.0.0
  author: Dennis A. Garcia
  hermes:
    tags: [tmforum, tmf, bss, oss, telecom, router]
    category: tmforum
---

# TMF Router

## When to Use
- The request mentions TM Forum, TMF, Frameworx, Open Digital Framework (ODF), BSS/OSS standards, or a document ID such as TMF622, GB921, IG1252, TMFC028.
- The request is ambiguous about which TMF framework applies.

## Procedure
1. Classify the request with this table. Load the matching skill.

| The request asks | Load skill |
|---|---|
| HOW the business operates. Process, workflow, Fulfillment, Assurance, Billing | `tmf-etom` |
| WHAT data exists. Entity, attribute, schema, data model | `tmf-sid` |
| WHICH functions or applications. App map, rationalization, RFP scope | `tmf-functional-framework` |
| HOW systems talk. API number, payload, REST design, events | `tmf-open-apis` |
| Target architecture. Components, cloud-native, Canvas, modernization | `tmf-oda` |
| Network automation level, closed loop, intent, zero-touch | `tmf-autonomous-networks` |
| Capability map, value stream, portfolio planning | `tmf-business-architecture` |
| A use case spanning two or more frameworks | `tmf-traceability` |
| Critique a design, RFP, roadmap, or vendor claim | `tmf-architecture-review` |

2. If two or more rows match, load `tmf-traceability` first. It sequences the others.
3. Resolve unfamiliar terms with `references/glossary.md`.
4. Every answer names the framework, the document ID, and the release it relies on.

## Reference loading
- Hermes: `skill_view("tmf-router", "references/glossary.md")`
- Claude: read `references/glossary.md` in this skill's directory.

## Pitfalls
- TMF frameworks are reference models. They are not mandatory implementation specs. Do not present them as law.
- TM Forum documents are member/RAND IPR. These skills hold structure and names only. For field-level detail, direct the user to the official specification. Do not reproduce spec text.
- Never fabricate an API number, document ID, entity name, or component ID. If unsure, write "verify in the TM Forum directory".
- Legacy names persist: Frameworx = core frameworks of the Open Digital Framework. TAM = Application Framework = Functional Framework. SID = Information Framework. eTOM = Business Process Framework.

## Verification
- The answer cites at least one TM Forum document ID or official URL.
- No claim depends on memory alone where a release number matters.
