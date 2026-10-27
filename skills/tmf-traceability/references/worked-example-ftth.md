# Worked Example: Residential FTTH Order

Use case: A residential customer orders a fiber broadband offer online and receives a working service and a first bill.
eTOM flow: Order to Payment.
Confidence column reflects these skills, not a client validation.

| # | eTOM process | Domain / vertical | SID entity | Function | Open API | ODA block | Confidence |
|---|---|---|---|---|---|---|---|
| 1 | Customer Interface Management, Selling | Customer / Fulfillment | ProductOffering (spec) | Product Catalog Management | TMF620 | Core Commerce | Reference |
| 2 | Selling (address and offer qualification) | Customer / Fulfillment | GeographicAddress, ProductOfferingQualification | Qualification | TMF673, TMF679, TMF645 | Core Commerce, Production | Reference |
| 3 | Selling (customer creation) | Customer / Fulfillment | Party, PartyRole Customer, BillingAccount | Customer Information Management | TMF632, TMF629, TMF666 | Party Management | Reference |
| 4 | Order Handling | Customer / Fulfillment | ProductOrder (instance) | Customer Order Management | TMF622 | Core Commerce | Reference |
| 5 | Service Configuration & Activation (decompose) | Service / Fulfillment | ServiceOrder, CFS, RFS | Service Order Management | TMF641 | Production | Reference |
| 6 | Resource Provisioning (assign port, VLAN, IP) | Resource / Fulfillment | Resource (logical, physical), ResourceOrder | Resource Inventory, Resource Order Management | TMF639, TMF652, TMF685 | Production | Reference |
| 7 | Workforce Management (installation) | Resource / Fulfillment | Appointment | Workforce Management | TMF646 | Production | Reference |
| 8 | Service Configuration & Activation (activate) | Service / Fulfillment | Service (instance) | Service Activation | TMF640, TMF702 | Production | Reference |
| 9 | Order Handling (complete), product instance created | Customer / Fulfillment | Product (instance) | Product Inventory | TMF637, TMF638 | Core Commerce, Production | Reference |
| 10 | Bill Invoice Management | Customer / Billing | CustomerBill | Bill Calculation | TMF678 | Core Commerce | Reference |

## Assurance loop attached to row 8
| Trigger | Observe | Analyze | Act | Ticket |
|---|---|---|---|---|
| ONT or OLT port alarm | TMF642 | Map alarm to Resource (TMF639), then Service (TMF638), then Customer | TMF702 reset or reconfigure | TMF621 if unresolved |

## Entity ownership
| SID entity | Master |
|---|---|
| ProductOffering | Product Catalog component |
| Party, Customer | Party Management component |
| ProductOrder | Product Order component |
| Service | Service Inventory component |
| Resource | Resource Inventory component |
