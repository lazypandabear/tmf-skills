# tmf-skills

Granular TM Forum framework skills for Hermes Agent and Claude. One skill per framework, plus a router, a cross-framework traceability skill, and an architecture review skill. Format follows the Agent Skills standard, so the same folders load in both agents.

## Skills
| Skill | Covers | Load when |
|---|---|---|
| `tmf-router` | Entry point, glossary | Any TMF request; unclear which framework |
| `tmf-etom` | Business Process Framework, GB921 | Process mapping, FAB, end-to-end flows |
| `tmf-sid` | Information Framework, GB922 | Data model, entities, legacy schema mapping |
| `tmf-functional-framework` | Functional/Application Framework (TAM), GB929 | App rationalization, RFP functional scope |
| `tmf-open-apis` | Open APIs, TMF630 design rules, CTK | API selection, payload design, conformance |
| `tmf-oda` | Open Digital Architecture, components, Canvas | Target architecture, migration |
| `tmf-autonomous-networks` | AN levels L0 to L5, closed loops, intent | Automation assessment and design |
| `tmf-business-architecture` | Capability Map GB1029C, Value Streams GB1029V | Capability heatmaps, portfolio planning |
| `tmf-traceability` | Capability to closed loop chain | Use cases spanning frameworks |
| `tmf-architecture-review` | Anti-pattern checklist | Design, RFP, or vendor claim review |

## Layout
```
skills/<skill-name>/SKILL.md            # short, procedural, under 4k chars
skills/<skill-name>/references/*.md     # loaded on demand
skills/<skill-name>/templates/*.md      # output templates
bundles/tmf-architect.yaml              # Hermes skill bundle
scripts/validate.py                     # checks Claude and Hermes rules
install.sh                              # Hermes, Claude Code, claude.ai zips
```

## Install

### Hermes Agent
Option A. Tap this repo (updates via `hermes skills check` and `hermes skills update`):
```bash
hermes skills tap add <owner>/tmf-skills
hermes skills install <owner>/tmf-skills/tmf-router
# repeat per skill, or install directly by path:
hermes skills install <owner>/tmf-skills/skills/tmf-etom
```
Option B. External directory (git pull updates everything; no copy):
```yaml
# ~/.hermes/config.yaml
skills:
  external_dirs:
    - ~/src/tmf-skills/skills
```
Hermes can edit skills under a writable external dir. Make the clone read-only if that matters.

Option C. Copy or symlink into a profile:
```bash
./install.sh --hermes                                   # default profile
./install.sh --hermes --hermes-home ~/.hermes-work      # another profile home
./install.sh --hermes --link                            # symlink instead of copy
```
Then use `/tmf-router ...` or the bundle `/tmf-architect ...`.

### Claude Code
```bash
./install.sh --claude-code          # ~/.claude/skills/
```

### claude.ai
```bash
./install.sh --zip                  # dist/<skill>.zip, one per skill
```
Upload each zip in claude.ai skills settings.

## Compatibility decisions
- `version` and `author` sit under `metadata`. Claude's validator rejects top-level `version`. Hermes reads `metadata.hermes.*` and does not require top-level `version`.
- Descriptions run 200 to 300 chars. Hermes `/learn` house style prefers 60 chars or less. Claude routing needs trigger words. Routing accuracy wins. Ten skills cost under 1k tokens in the Hermes skill index.
- Every SKILL.md names its reference files in backticks. Hermes URL installs copy only referenced files.
- Each SKILL.md gives both loading forms: Hermes `skill_view(name, path)` and Claude relative read.

Validate before every push:
```bash
pip install pyyaml && python scripts/validate.py
```

## Corrections to the source summary these skills were built from
- eTOM: Fulfillment, Assurance, Billing are vertical end-to-end groupings inside Operations. Horizontals are the functional domains (Market/Sales, Product, Customer, Service, Resource, Partner, Enterprise). The summary inverted this.
- eTOM SIP verticals are Strategy & Commit, Infrastructure Lifecycle Management, Product Lifecycle Management. "Strategy, Infrastructure, Product" is the Level 0 area, not three layers.
- TAM: no longer an application list in practice. It became a function-level decomposition (GB929F) because CSP application boundaries do not match it. Map functions, not applications.
- ODA does not replace eTOM and SID. It references them and adds a functional architecture, component model, and runtime.
- Open APIs are not REST-only. Event notifications via hub are part of the pattern. "Cuts integration timelines" is an unquantified vendor claim.
- Capability Map (Beta) and Value Stream Framework (early-stage) are not stable standards. Treat outputs from them as provisional.
- "AI-driven" carries no testable meaning. The skills replace it with named Intelligence Management functions and KPIs.

## IP note
These skills contain structure, names, and methods. They do not reproduce TM Forum specification text. For attribute-level detail, use the official documents (most are RAND, member access).

## Sources
- Hermes Agent skills system: https://hermes-agent.nousresearch.com/docs/user-guide/features/skills
- Hermes working with skills: https://hermes-agent.nousresearch.com/docs/guides/work-with-skills
- GB929 Application Framework (TAM) Suite v25.0: https://www.tmforum.org/resources/suite/gb929-application-framework-tam-suite-v25-0
- GB929 R14.5.1 (shift to functional decomposition): https://www.tmforum.org/resources/suite/gb929-application-framework-r14-5-1
- GB921D domain-based decomposition: https://tmforum.org/resources/standard/gb921d-l3-process-decomposition-r18-0
- TMF630 API Design Guidelines 4.0.1: https://www.tmforum.org/resources/standard/tmf630-api-design-guidelines-4-0/
- ODA Component design guidelines: https://github.com/tmforum-oda/oda-ca-docs/blob/master/ODAComponentDesignGuidelines.md
- TMFC028 Party Management component: https://www.tmforum.org/oda/directory/components-map/party-management/TMFC028
- IG1167 ODA Functional Architecture: https://www.tmforum.org/resources/standard/ig1167-oda-functional-architecture-exploratory-report-v6-0-0
- IG1252 AN Levels Evaluation Methodology: https://www.tmforum.org/resources/standard/ig1252-autonomous-network-levels-evaluation-methodology-1-0-0/
- Nokia Bell Labs, AN current state: https://nokia.com/bell-labs/bell-labs-consulting/articles/autonomous-networks-what-is-the-current-state-and-how-to-move-forward
- Value Stream Framework: https://www.tmforum.org/oda/value-stream-framework
- GB1029C Capability Map v3.0.4: https://www.tmforum.org/resources/standard/tm-forum-capability-map-v3-0-4-gb1029c
- GB1029V Value Stream Framework v1.0.4: https://tmforum.org/resources/standard/gb1029v-tm-forum-value-stream-framework-v1-0-4
