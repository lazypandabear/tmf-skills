# AN Architecture, Closed Loops, and Intent

## Layers
```
Business operations   -- intent -->   Service operations   -- intent -->   Resource operations
  (closed loop 3)        <- report --   (closed loop 2)       <- report --   Autonomous domains
                                                                             (access | transport | core,
                                                                              per region or vendor)
                                                                              (closed loop 1)
```

## Closed-loop design template
| Element | Content |
|---|---|
| Trigger | Alarm, KPI threshold, prediction, intent change |
| Observe | Data sources and APIs (TMF642 alarms, TMF628 performance, TMF639 inventory) |
| Analyze | Correlation, root cause, impact on services (TMF638) and customers |
| Decide | Policy or model; approval gate if level below L4 for this task |
| Act | Domain controller call, TMF640 or TMF702 activation, ticket TMF621 if human needed |
| Verify | Post-action KPI check within a set window |
| Rollback | Automatic revert condition and method |
| Audit | Log decision inputs, model version, action, outcome |

## Intent
- An intent states the expected outcome and constraints. Example: "Keep packet loss under 0.1 percent for enterprise VPN customers in Region North."
- The receiving layer reports fulfillment status and deviations.
- API: TMF921 Intent Management. Models: IG1253 intent guide.

## Prerequisites checklist
- Resource inventory accuracy measured and above an agreed threshold.
- Topology links service instances to resources.
- Alarms deduplicated and correlated.
- Programmable access to domain controllers.
- Change management integration (TMF655).
