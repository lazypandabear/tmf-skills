# Open API Conformance

## What a CTK does
- Runs against a live endpoint.
- Reads the base path from the declared OAS file to choose which API CTK to run.
- Tests mandatory resources, operations, attributes, and response codes from the conformance profile.

## Evidence to demand from a vendor
| Claim | Acceptable evidence |
|---|---|
| "Supports TMF622" | CTK report for the stated version against the vendor's endpoint, dated |
| "Certified" | Listing in TM Forum's conformance directory for that API and version |
| "ODA Component" | Component listing with component ID, plus component CTK result (see `tmf-oda`) |
| "Extended TMF API" | Published extension schema at `@schemaLocation`; base CTK still passes |

## Internal procedure
1. Pin the API version in the integration contract.
2. Validate every payload in CI against the official OAS schema.
3. Run the CTK in a test environment before each release.
4. Track optional features used; they are not covered by mandatory CTK checks.

## Red flags
- A PDF claiming conformance with no CTK output.
- A conformance claim for a version the vendor's endpoint path does not expose.
- "TMF-like" or "TMF-inspired" APIs presented as standard.
