# TMF630 Design Rules: Checklist

TMF630 parts:
1. Naming, CRUD, filtering, notifications.
2. Polymorphism, extension patterns, depth and expand, RefOrValue.
3. Hypermedia support.
4. Lifecycle management, common tasks.
5. JSON Patch extension for arrays.
6. JSON Path extension.
7. JSON Schema patterns.

## Checklist
| Area | Rule |
|---|---|
| Path | `/tmf-api/{apiName}/v{major}/{resource}`. Major version only in path. |
| Resource names | camelCase, singular resource name (`productOrder`). |
| IDs | Server assigns `id` and `href`. Clients never set them on create. |
| Create | `POST /{resource}` returns 201 with the full representation. |
| Retrieve | `GET /{resource}/{id}`; `GET /{resource}` for lists. |
| Partial update | `PATCH` with `application/merge-patch+json`. JSON Patch (`application/json-patch+json`) for array operations where supported. |
| Delete | `DELETE /{resource}/{id}` returns 204. |
| Attribute selection | `?fields=id,state` returns only listed attributes. |
| Filtering | Query on attributes, e.g. `?state=completed`. |
| Pagination | `offset` and `limit`. Count headers per spec version (`X-Total-Count`, `X-Result-Count`). |
| Polymorphism | Every entity carries `@type`. Subclasses add `@baseType` and `@schemaLocation`. |
| References | `{ "id", "href", "@referredType" }`. Use RefOrValue where the spec allows embedding. |
| Extension | Add characteristics first. Subclass via `@type` and publish the schema at `@schemaLocation`. |
| Tasks | Operations that are not CRUD become task resources, e.g. `cancelProductOrder`. |
| Lifecycle | `state` or `lifecycleStatus` follows the state machine in the spec. |
| Events | `POST /hub` registers a listener callback. Events: create, attributeValueChange, stateChange, delete. |
| Errors | Standard HTTP codes plus the TMF error body (`code`, `reason`, `message`, `status`). |

## Minimal payload shape (illustrative, not normative)
```json
{
  "@type": "ProductOrder",
  "productOrderItem": [
    {
      "id": "1",
      "action": "add",
      "@type": "ProductOrderItem",
      "productOffering": { "id": "PO-FIBER-500", "@referredType": "ProductOffering" }
    }
  ],
  "relatedParty": [
    { "role": "Customer", "partyOrPartyRole": { "id": "C-1001", "@referredType": "Customer" } }
  ]
}
```
The `relatedParty` shape differs between v4 and v5. Check the target version's OAS.
