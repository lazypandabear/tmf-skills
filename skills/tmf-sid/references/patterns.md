# SID Core Patterns

## 1. Specification vs instance
- Specification: reusable definition. Lives in a catalog. Example: ProductSpecification, ServiceSpecification, ResourceSpecification.
- Instance: a concrete occurrence created from a specification. Example: Product, Service, Resource.
- Product side adds a commercial layer:

```
ProductOffering  -- sells -->  ProductSpecification
     |                               |
  ProductOfferingPrice         (instantiated as)
                                     v
                                  Product  -- owned by --> Party (in role Customer)
```

## 2. Party and PartyRole
```
Party (Individual | Organization)
  └── PartyRole (Customer, Supplier, Partner, Employee, ...)
        └── Account (billing/financial), Agreement, ContactMedium
```
- Store identity once on Party. Store relationship-specific data on PartyRole.

## 3. Product, Service, Resource chain
```
Product                      (what the customer owns)
  └── realized by CFS        (Customer Facing Service; customer-visible)
        └── realized by RFS  (Resource Facing Service; internal)
              └── uses Resource (logical: VLAN, IP, port; physical: OLT, ONT, card)
```
- Catalog side mirrors it: ProductSpecification references CFS specifications; CFS specifications reference RFS specifications; RFS specifications reference ResourceSpecifications.
- FTTH example: Product "Fiber 500 Mbps". CFS "Internet Access". RFS "GPON Access", "IP Connectivity". Resources: OLT port, ONT, VLAN, IP pool.

## 4. Characteristics
- CharacteristicSpecification defines name, value type, allowed values.
- CharacteristicValue carries the instance value.
- Use characteristics to extend without schema changes. Subclass only when lifecycle or behavior differs.

## 5. Business Interaction
- Orders, requests, inquiries, and problems are Business Interactions with Business Interaction Items.
- ProductOrder, ServiceOrder, ResourceOrder, TroubleTicket follow this shape: header plus items plus state.

## Mapping to Open APIs
| Pattern | Typical API resource |
|---|---|
| ProductOffering, ProductSpecification | TMF620 productOffering, productSpecification |
| Product | TMF637 product |
| CFS/RFS specification, Service | TMF633 serviceSpecification, TMF638 service |
| ResourceSpecification, Resource | TMF634 resourceSpecification, TMF639 resource |
| Party, PartyRole | TMF632 individual/organization, TMF669 partyRole |
| Business Interaction (orders) | TMF622 productOrder, TMF641 serviceOrder, TMF652 resourceOrder |
