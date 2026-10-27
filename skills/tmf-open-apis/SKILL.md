---
name: tmf-open-apis
description: "TM Forum Open APIs (TMF6xx, TMF7xx, TMF9xx). Use to pick the right API by number, design TMF-conformant REST resources and event notifications, map payloads to SID, or plan conformance testing (CTK). Covers TMF630 design rules and v4 vs v5 differences."
license: MIT
compatibility: "Agent Skills standard. Works in Hermes Agent and Claude. Knowledge-only; web access helps for fetching official OAS files."
metadata:
  version: 1.0.0
  author: Dennis A. Garcia
  hermes:
    tags: [tmforum, open-api, rest, tmf630, tmf622, tmf620, integration, ctk]
    category: tmforum
---

# TMF Open APIs

## When to Use
- Choose the API for an integration. Example: "Which API places a service order?"
- Design or review a REST resource, payload, or event against TMF rules.
- Plan conformance testing or evaluate a vendor's API claim.

## Core Model
- Each API carries a number (TMF622 Product Ordering) and a resource model derived from SID.
- Base path pattern: `/tmf-api/{apiName}/v{major}/{resource}`. Example: `/tmf-api/productCatalogManagement/v4/productOffering`.
- Polymorphism and extension use `@type`, `@baseType`, `@schemaLocation`.
- References use `id`, `href`, `@referredType`. RefOrValue allows a reference or an embedded value.
- Notifications use a hub: the client registers a callback via `POST /hub`; the server pushes events such as create, attribute value change, state change, delete.
- Design rules live in TMF630 (seven parts). Load `references/design-rules.md`.

## Procedure: choose an API
1. Identify the entity with `tmf-sid`.
2. Look up the API in `references/api-catalog.md`.
3. Confirm current version and status in the TM Forum Open API directory or GitHub. Do not assume.
4. Read the conformance profile: mandatory vs optional resources, operations, attributes.
5. Extend via `@type` subclass and characteristics. Do not fork the schema.

## Procedure: review an implementation
1. Check path, resource names, and HTTP methods against the official OAS file.
2. Check `@type` presence, reference format, filtering, pagination, PATCH media types.
3. Check event hub support and event payload shape.
4. Require a CTK report. Load `references/conformance.md`.

## Reference loading
- Hermes: `skill_view("tmf-open-apis", "references/api-catalog.md")`
- Claude: read `references/api-catalog.md` in this skill's directory.

## Pitfalls
- API washing: a proprietary API with TMF names but non-conformant schema. Conformance requires a CTK pass.
- Mixing v4 and v5 in one contract without mediation. v5 moved to OpenAPI 3 and restructured schemas.
- Custom top-level attributes instead of characteristics or `@type` extension. Breaks interoperability.
- Point-to-point calls between components that bypass the decoupling layer. Use the gateway or event bus.
- Never invent an API number. If missing from the catalog, say "verify in the Open API directory".

## Verification
- API number, name, and version stated.
- Payload validates against the official OAS schema.
- CTK result attached or flagged as missing.
