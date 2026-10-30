# 4. Implementation blueprint

## Delivery approach

Implement the capability in measurable increments. Start with visibility and evidence; introduce remediation automation only after inventory, ownership and guardrails are reliable.

## Phase 0 — Establish the baseline
- Agree scope: cloud accounts, subscriptions, projects, data centres and business services.
- Identify authoritative asset and ownership sources.
- Define severity policy, risk factors, change gates and exception process.
- Baseline asset coverage, time to identify, time to remediate and verified closure.
- Select a limited pilot technology/service group.

**Exit criteria:** documented scope, accountable owners, data sources and measurable baseline.

## Phase 1 — Centralise discovery
- Integrate vulnerability scanner, cloud inventory, CMDB and container registry.
- Ingest vendor advisories and exploit intelligence.
- Establish canonical asset and component identities.
- Track inventory freshness and confidence.
- Build initial exposure dashboard.

**Exit criteria:** pilot assets can be correlated to findings with source evidence and owners.

## Phase 2 — Contextual prioritisation
- Add reachability, business criticality and data classification.
- Correlate SBOM components with deployed workloads.
- Identify duplicate findings and false-positive patterns.
- Implement explainable prioritisation and SLA policy.
- Route findings to accountable teams.

**Exit criteria:** prioritised work items include affected assets, rationale, owner and remediation guidance.

## Phase 3 — Guarded remediation automation
- Create platform-specific runbooks.
- Integrate ITSM and change management.
- Automate lower-environment patch/rebuild/test.
- Add approvals, canary/rolling deployment and rollback.
- Start with a small set of low-risk, repeatable changes.

**Exit criteria:** approved changes execute consistently with complete audit records.

## Phase 4 — Verified closure and scale
- Validate running versions and deployed image digests.
- Re-scan after remediation.
- Reopen failed or regressed findings automatically.
- Extend to additional clouds, clusters, platforms and business services.
- Introduce exception ageing and executive risk reporting.

**Exit criteria:** end-to-end evidence demonstrates risk closure and ongoing drift detection.

## Pilot selection

Choose a pilot with:
- Clear asset ownership.
- Representative but bounded technology scope.
- Existing scanner and deployment pipeline.
- Non-production environment.
- Repeatable patch path.
- Defined service health tests.
- Business sponsor and change approver.

## Acceptance criteria

A pilot is successful when:
1. A new advisory is ingested with traceable source data.
2. Matching assets are identified with confidence and freshness.
3. Risk rationale is explainable.
4. Work is routed to an accountable owner.
5. Approved remediation executes through the existing delivery process.
6. The deployed state is independently validated.
7. Evidence is linked to the work item.
8. Failed validation causes escalation/reopen, not false closure.
