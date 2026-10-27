# TMF Anti-Pattern Checklist

| Area | Anti-pattern | Detection signal | Default severity | Fix |
|---|---|---|---|---|
| Process | FAB drawn as horizontal layers | Diagram puts Fulfillment, Assurance, Billing as rows | Minor | Redraw: FAB are OPS verticals; domains are horizontals |
| Process | eTOM used as org chart | Departments named after L1 boxes | Major | Keep eTOM as classification; design org by value stream |
| Process | No L2 mapping | Processes described only in vendor terms | Major | Map each process to eTOM L2 with release |
| Data | Multiple masters | Two systems create or edit the same customer or catalog record | Blocker | Assign one system of record per SID ABE |
| Data | Customer equals Party | One table holds identity and role data | Major | Split Party and PartyRole |
| Data | SID as physical schema | Database mirrors SID class diagram 1:1 | Major | Logical model in SID; physical model optimized per component |
| Data | Offering, specification, product conflated | One "product" table holds price, tech spec, and customer instance | Blocker | Separate ProductOffering, ProductSpecification, Product |
| Functions | Vendor module equals TAM box | Mapping lists products, not functions | Major | Decompose to functions (GB929F) |
| APIs | API washing | TMF names on endpoints, no CTK report | Blocker if contractual | Require CTK per API and version |
| APIs | Version mixing | v4 and v5 payloads in one contract | Major | Pin version; mediate at gateway |
| APIs | Top-level custom fields | Non-standard attributes outside characteristics or @type | Major | Move to characteristics or published subclass |
| APIs | Point-to-point mesh | Components call each other directly | Major | Route via Decoupling & Integration layer |
| ODA | Monolith relabeled as components | Single deployable unit with many TMF APIs | Major | Define components with independent deployment and declared dependencies |
| ODA | Big-bang replacement | Roadmap swaps the full stack at once | Blocker | Decouple first; replace one component at a time |
| ODA | No component spec | No exposed and dependent API list | Major | Write component spec per IG1171 structure |
| AN | Network-wide level claim | "We are L4" without scope | Major | Assess per workflow and domain per IG1252 |
| AN | Automation on dirty inventory | No inventory accuracy metric | Blocker | Measure and fix inventory before closed loops |
| AN | No guardrails | No approval gate, rollback, or audit | Blocker | Add guardrails per closed-loop template |
| Business architecture | Capability equals process | Capability names are verbs or process names | Minor | Rename capabilities as stable nouns |
| Business architecture | Map not tied to money | Heatmap has no investment link | Major | Add investment backlog |
| Claims | "Fully TMF compliant" | No API, version, or certificate named | Major | Request evidence per framework and release |
| Claims | "ODA-ready" | No directory listing or component CTK | Major | Request listing and CTK output |
| Claims | "AI-driven" | No defined function, data source, or metric | Minor | Specify the Intelligence Management function and KPI |
