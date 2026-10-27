---
name: tmf-sid
description: "TM Forum Information Framework (SID, GB922). Use to model, name, or map telecom data: domains, Aggregate Business Entities (ABEs), specification vs instance, Party and PartyRole, the Product-Service-Resource chain, characteristics. Use for schema design and legacy data mapping."
license: MIT
compatibility: "Agent Skills standard. Works in Hermes Agent and Claude. Knowledge-only; no tools required."
metadata:
  version: 1.0.0
  author: Dennis A. Garcia
  hermes:
    tags: [tmforum, sid, gb922, data-model, information-framework]
    category: tmforum
---

# SID: Information Framework (GB922)

## When to Use
- Design a data model or API payload for BSS/OSS.
- Map a legacy schema (CRM, billing, inventory, ERP) to industry entities.
- Resolve naming disputes between teams or vendors.

## Core Model
- Domains: Market/Sales, Product, Customer, Service, Resource, Supplier/Partner (Business Partner in newer releases), Enterprise, Common Business (Common).
- Each domain holds ABEs. ABEs decompose into entities. High cohesion inside a domain, loose coupling between domains.
- SID domains align with eTOM domains. SID L1 ABEs map to eTOM L2 processes.
- Four patterns carry most of the model. Load `references/patterns.md`:
  1. Specification vs instance.
  2. Party and PartyRole.
  3. Product realized by CFS, CFS realized by RFS, RFS realized by Resource.
  4. Characteristic specification and characteristic value.

## Procedure: map a legacy schema
1. Inventory source tables or objects.
2. Assign each to one domain. The domain is the one that owns the object's lifecycle.
3. Decide specification (catalog, template) or instance (owned, deployed, billed).
4. Map to ABE and entity. Load `references/domains-abes.md`.
5. Record gaps. Extend with characteristics first. Subclass only when behavior differs.
6. When the object is exposed by API, align names with the Open API resource model. Open API models derive from SID. Hand off to `tmf-open-apis`.
7. Output this table:

| Source object | SID domain | ABE | Entity | Spec or instance | Extension | Confidence |
|---|---|---|---|---|---|---|

## Reference loading
- Hermes: `skill_view("tmf-sid", "references/patterns.md")`
- Claude: read `references/patterns.md` in this skill's directory.

## Pitfalls
- SID is a logical model, not a physical database schema. A 1:1 implementation over-normalizes and kills performance.
- Customer is a PartyRole, not a Party. One person or organization can hold many roles.
- Product Offering (what is sold, with price and terms) differs from Product Specification (what it is) and Product (the instance a customer owns).
- Billing Account is separate from Customer.
- Never invent SID entity names. Mark unknowns "verify in GB922".

## Verification
- Every target entity cites domain and ABE.
- Every row states spec or instance.
- Extensions are listed separately from standard entities.
