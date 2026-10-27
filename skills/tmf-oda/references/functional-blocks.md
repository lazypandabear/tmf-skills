# ODA Functional Blocks

Component names are representative. Get exact component IDs (TMFCxxx) from the ODA Component Directory. Only TMFC028 is stated here because it was verified.

| Block | Scope | Representative components | Key APIs |
|---|---|---|---|
| Engagement Management | Channels and user interaction for people and systems: portals, apps, chat, partner channels | Digital channel front-ends, Party Interaction | TMF683, TMF681 |
| Party Management | Parties, roles, relationships, accounts, privacy, identity | Party Management (TMFC028), Party Privacy, Party Interaction, Digital Identity | TMF632, TMF669, TMF666, TMF644 |
| Core Commerce Management | Catalog, offers, quotes, carts, product orders, product inventory, agreements, SLAs, billing and charging | Product Catalog Management, Product Order Capture & Validation, Product Order Delivery Orchestration, Product Inventory, Billing Account Management, Bill Calculation | TMF620, TMF622, TMF637, TMF648, TMF663, TMF678 |
| Production | Delivery and lifecycle of customer facing and resource facing services and resources | Service Catalog, Service Order Management, Service Inventory, Resource Catalog, Resource Order Management, Resource Inventory, Activation | TMF633, TMF641, TMF638, TMF634, TMF652, TMF639, TMF640, TMF702 |
| Intelligence Management | Analytics on operational data, AI/ML models, closed-loop control | Analytics, AI model management, closed-loop controllers | TMF628, TMF649, TMF921 |
| Decoupling & Integration | Keeps block boundaries intact: API gateway, event bus, API exposure and management | Gateway, event hub, process flow | TMF688, TMF701 |

## Verified example
TMFC028 Party Management. Block: Party Management. Mandatory exposed API: TMF632. Optional: TMF688, TMF701.

## Mapping rule
- One SID ABE has one master component.
- A component's exposed APIs must match the entities it masters.
