# Open API Catalog (core set)

Numbers and names only. Versions and status change each release. Confirm in the TM Forum Open API directory or the official GitHub repositories before implementation.

## Party and Engagement
| API | Name | Main resources |
|---|---|---|
| TMF629 | Customer Management | customer |
| TMF632 | Party Management | individual, organization |
| TMF669 | Party Role Management | partyRole |
| TMF666 | Account Management | billingAccount, partyAccount, financialAccount |
| TMF683 | Party Interaction Management | partyInteraction |
| TMF681 | Communication Management | communicationMessage |
| TMF646 | Appointment Management | appointment, searchTimeSlot |
| TMF644 | Privacy Management | partyPrivacyProfile, partyPrivacyAgreement |
| TMF691 | Federated ID | user info |
| TMF672 | User Roles and Permissions | permission, userRole |
| TMF668 | Partnership Management | partnership |

## Product and Commerce
| API | Name | Main resources |
|---|---|---|
| TMF620 | Product Catalog Management | catalog, category, productOffering, productSpecification, productOfferingPrice |
| TMF622 | Product Ordering Management | productOrder, cancelProductOrder |
| TMF637 | Product Inventory Management | product |
| TMF679 | Product Offering Qualification | checkProductOfferingQualification, queryProductOfferingQualification |
| TMF648 | Quote Management | quote |
| TMF663 | Shopping Cart | shoppingCart |
| TMF671 | Promotion Management | promotion |
| TMF680 | Recommendation Management | recommendation |
| TMF760 | Product Configuration Management | checkProductConfiguration, queryProductConfiguration |
| TMF651 | Agreement Management | agreement, agreementSpecification |
| TMF623 | SLA Management | sla, slaViolation |
| TMF658 | Loyalty Management | loyaltyProgram, loyaltyAccount |

## Billing and Revenue
| API | Name | Main resources |
|---|---|---|
| TMF678 | Customer Bill Management | customerBill, appliedCustomerBillingRate |
| TMF676 | Payment Management | payment, refund |
| TMF670 | Payment Methods | paymentMethod |
| TMF654 | Prepay Balance Management | bucket, topupBalance |
| TMF635 | Usage Management | usage, usageSpecification |
| TMF677 | Usage Consumption Management | queryUsageConsumption |

## Service
| API | Name | Main resources |
|---|---|---|
| TMF633 | Service Catalog Management | serviceCatalog, serviceSpecification |
| TMF641 | Service Ordering Management | serviceOrder |
| TMF638 | Service Inventory Management | service |
| TMF645 | Service Qualification | checkServiceQualification, queryServiceQualification |
| TMF640 | Service Activation and Configuration | service, monitor |
| TMF657 | Service Quality Management | serviceLevelObjective, serviceLevelSpecification |
| TMF653 | Service Test Management | serviceTest, serviceTestSpecification |
| TMF656 | Service Problem Management | serviceProblem |

## Resource
| API | Name | Main resources |
|---|---|---|
| TMF634 | Resource Catalog Management | resourceCatalog, resourceSpecification |
| TMF652 | Resource Ordering Management | resourceOrder |
| TMF639 | Resource Inventory Management | resource |
| TMF702 | Resource Activation Management | resource, monitor |
| TMF664 | Resource Function Activation and Configuration | resourceFunction |
| TMF685 | Resource Pool Management | resourcePool, availabilityCheck, reservation |
| TMF642 | Alarm Management | alarm |
| TMF628 | Performance Management | performanceIndicatorSpecification, measurementCollectionJob |
| TMF649 | Performance Thresholding | threshold |

## Assurance, Location, Common
| API | Name | Main resources |
|---|---|---|
| TMF621 | Trouble Ticket Management | troubleTicket |
| TMF655 | Change Management | changeRequest |
| TMF673 | Geographic Address Management | geographicAddress, geographicAddressValidation |
| TMF674 | Geographic Site Management | geographicSite |
| TMF675 | Geographic Location Management | geographicLocation |
| TMF667 | Document Management | document |
| TMF662 | Entity Catalog Management | entitySpecification |
| TMF688 | Event Management | event, topic, hub |
| TMF701 | Process Flow Management | processFlow, taskFlow |
| TMF687 | Stock Management | productStock |
| TMF684 | Shipment Tracking Management | shipmentTracking |
| TMF921 | Intent Management | intent, intentReport |

## Design guidelines
| Doc | Content |
|---|---|
| TMF630 | REST API Design Guidelines, parts 1 to 7 |
