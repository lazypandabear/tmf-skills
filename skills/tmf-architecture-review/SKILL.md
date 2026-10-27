---
name: tmf-architecture-review
description: "Stress-test a BSS/OSS architecture, RFP, vendor proposal, or roadmap against TM Forum frameworks. Use when asked to review, audit, critique, or score TMF alignment. Detects common anti-patterns and unverifiable compliance claims, and returns severity-ranked findings."
license: MIT
compatibility: "Agent Skills standard. Works in Hermes Agent and Claude. Knowledge-only; no tools required."
metadata:
  version: 1.0.0
  author: Dennis A. Garcia
  hermes:
    tags: [tmforum, architecture-review, audit, rfp, vendor-evaluation, anti-patterns]
    category: tmforum
---

# TMF Architecture Review

## When to Use
- Review a solution design, target architecture, or roadmap.
- Evaluate a vendor proposal or RFP response that claims TM Forum alignment.
- Score a program's TMF maturity before a steering decision.

## Procedure
1. Collect the artifact. Note its scope, date, and author.
2. Run the checklist in `references/anti-patterns.md`, section by section: process, data, functions, APIs, ODA, AN, business architecture, claims.
3. For each hit, record: finding, evidence (page or line), severity, fix.
   - Blocker: breaks integration, data integrity, or contractual conformance.
   - Major: adds cost or lock-in; fix before build.
   - Minor: naming or documentation gap.
4. For every compliance claim, demand evidence: CTK report, directory listing, assessment certificate. No evidence means "unverified".
5. Output:
   - Findings table sorted by severity.
   - Top 3 fixes with owner and effort band.
   - Unverified claims list.
6. Hand detailed fixes to the owning skill: `tmf-etom`, `tmf-sid`, `tmf-open-apis`, `tmf-oda`, `tmf-autonomous-networks`.

## Output template
| # | Area | Finding | Evidence | Severity | Fix |
|---|---|---|---|---|---|

## Reference loading
- Hermes: `skill_view("tmf-architecture-review", "references/anti-patterns.md")`
- Claude: read `references/anti-patterns.md` in this skill's directory.

## Pitfalls
- Softening findings to protect a vendor or sponsor. State the defect and the impact.
- Scoring alignment by vocabulary. Label matching is not conformance.
- Reviewing without the release numbers in scope. Pin releases first.

## Verification
- Every finding cites evidence from the artifact.
- Every compliance claim is marked verified or unverified.
