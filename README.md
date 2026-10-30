# Enterprise Security Vault

**Problem → Scale → Solution → Automation**

A solution-architecture reference for reducing the time between vulnerability disclosure and verified remediation across hybrid and multi-cloud environments.

> This repository is organised around the enterprise problem and the operating model required to solve it—not around a catalogue of security products.

## 1. Problem statement

Enterprise technology estates are distributed across cloud accounts, subscriptions, regions, Kubernetes clusters, virtual machines, container registries, SaaS platforms, source repositories and third-party dependencies.

When a critical vulnerability is disclosed, organisations often cannot answer four questions quickly and with evidence:

1. **Where are we exposed?** Asset inventories, SBOMs, runtime versions and ownership data are fragmented.
2. **How serious is our exposure?** CVSS alone does not describe reachability, exploitability, business criticality or compensating controls.
3. **Who must act?** Ownership is split across application, platform, cloud, security and service teams.
4. **Has the risk actually been removed?** A closed ticket or successful pipeline does not prove that every running workload is patched and healthy.

The result is a gap between vulnerability discovery and verified remediation.

## 2. How big is the problem?

The scale is not simply the number of CVEs. It is the number of assets, versions, dependencies, owners and deployment locations that must be correlated for each advisory.

A single enterprise application may exist as:
- Multiple production and non-production deployments.
- Several container image versions and base images.
- Multiple runtime versions across services and functions.
- Shared ingress, proxy and CI/CD components.
- Transitive open-source dependencies.
- Disaster-recovery and dormant environments.

**Measure the operational scale using your own inventory:**
- Total managed assets and workloads.
- Assets with unknown or stale ownership.
- Number of unique vulnerable components and versions.
- Internet-exposed vulnerable assets.
- Critical business services affected.
- Mean time to identify (MTTI).
- Mean time to remediate (MTTR).
- Percentage of fixes independently verified.
- Exceptions past their expiry date.

Do not publish an unsupported global asset count or claim that every installation is vulnerable. Exposure must be established from vendor advisories, asset evidence and configuration.

## 3. Proposed solution

Implement a centralised Vulnerability Exposure and Remediation capability that connects existing security, cloud, ITSM and engineering platforms.

**Target operating flow**

`Advisory → Asset correlation → Exposure analysis → Risk prioritisation → Remediation orchestration → Verification → Continuous monitoring`

Core capabilities:
- **Intelligence ingestion:** Vendor advisories, CVE/NVD data, CISA KEV and trusted threat intelligence.
- **Asset correlation:** CMDB, cloud inventory, Kubernetes, endpoint and container registry data.
- **Dependency correlation:** SBOM, package manifests, image layers and runtime evidence.
- **Contextual risk:** CVSS + exploit status + reachability + business criticality + exposure + compensating controls.
- **Ownership and workflow:** Service ownership, assignment, SLA, change approval and exception handling.
- **Remediation:** Patch, rebuild, redeploy, mitigate or isolate through approved runbooks.
- **Evidence:** Before/after versions, image digests, scan results, health checks and ticket references.

## 4. How to automate it

Automate the repeatable control loop while retaining human approval for high-impact production changes.

1. Ingest a new advisory and normalise its CVE/product/version/configuration data.
2. Enrich it with severity, exploit intelligence, vendor fixed versions and publication timestamps.
3. Query asset inventory, SBOMs, registries and runtime telemetry for matches.
4. Calculate contextual risk and identify affected business services.
5. Create or update a single remediation work item per accountable service/asset group.
6. Select an approved remediation runbook based on platform and deployment type.
7. Test patches in lower environments and run security/regression checks.
8. Obtain change approval where required; deploy through existing CI/CD or patch orchestration.
9. Re-scan and verify the running workload—not only the source repository or build artifact.
10. Close the work item only when evidence meets the acceptance criteria; otherwise reopen, escalate or apply a time-bound exception.

See [the automation reference architecture](docs/automation-reference-architecture.md) and [the implementation blueprint](docs/implementation-blueprint.md).

## 5. Architecture principles

- Cloud-agnostic control plane; platform-native execution.
- One asset identity and accountable owner wherever possible.
- API/event-driven integration; avoid brittle point-to-point scripts.
- Least privilege, workload identity and secrets management.
- Immutable audit trail and evidence retention.
- Risk-based prioritisation rather than CVSS-only sorting.
- Progressive delivery, rollback and production change controls.
- Human-in-the-loop approval for disruptive or high-risk actions.
- Continuous reconciliation to detect drift and reintroduced vulnerabilities.

## 6. Success measures

| Measure | What it proves |
|---|---|
| Asset coverage | Inventory completeness |
| Advisory-to-asset match rate | Discovery effectiveness |
| Time to identify | Speed of exposure discovery |
| Time to assign owner | Accountability |
| Time to remediate | Delivery effectiveness |
| Verified remediation rate | Actual risk reduction |
| Recurrence rate | Quality and durability of fixes |
| Exception ageing | Governance effectiveness |

Set baselines first, then agree targets by severity and business criticality. Do not invent universal SLAs.

## 7. Repository map

- `docs/problem-and-scale.md` — enterprise problem and how to quantify it.
- `docs/solution-architecture.md` — target capabilities and architecture.
- `docs/automation-reference-architecture.md` — event-driven automation and guardrails.
- `docs/implementation-blueprint.md` — phased implementation plan.
- `docs/cloud-control-mapping.md` — AWS, Azure, GCP and OCI capability mapping.
- `docs/operating-model-and-kpis.md` — roles, controls and measurable outcomes.

## Scope and disclaimer

This repository is an independent architecture reference. It does not assert that a product or environment is affected without verification. Always use the applicable vendor advisory, supported release guidance and environment-specific evidence before making production changes.
