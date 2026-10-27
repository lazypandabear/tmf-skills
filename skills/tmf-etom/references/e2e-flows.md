# eTOM End-to-End Flows

Flow names follow the GB921 end-to-end business flow addendum (GB921E). Verify names against the target release.

| Flow | Trigger | Main L2 touchpoints in order |
|---|---|---|
| Request to Answer | Customer inquiry | Customer Interface Management, Selling or Problem Handling, Customer Interface Management |
| Order to Payment | Customer order | Selling, Order Handling, Service Configuration & Activation, Resource Provisioning, Bill Invoice Management, Bill Payments & Receivables Management |
| Usage to Payment | Network usage | Resource Mediation & Reporting, Service Guiding & Mediation, Bill Invoice Management, Bill Payments & Receivables Management |
| Request to Change | Change request on existing product | Order Handling, Service Configuration & Activation, Resource Provisioning |
| Problem to Solution (Trouble to Resolve) | Customer or network fault | Problem Handling, Service Problem Management, Resource Trouble Management, Workforce Management, Problem Handling (closure) |
| Termination to Confirmation | Cease request | Order Handling, Service Configuration & Activation, Resource Provisioning, Bill Invoice Management (final bill) |
| Concept to Market | New product idea | SIP Product Lifecycle Management: offer development, service development, resource development, launch |

## Use
1. Pick the flow matching the user's journey.
2. List each L2 touchpoint with its domain and vertical.
3. Pass each touchpoint to `tmf-traceability` to attach SID entities and Open APIs.
