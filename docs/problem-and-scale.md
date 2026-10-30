# 1. Problem statement and enterprise scale

## The problem

A vulnerability disclosure creates an enterprise-wide correlation problem.

The advisory describes a vulnerable product, version range, configuration or dependency. The enterprise must determine which deployed assets match that condition, whether the vulnerable code path is reachable, what business service is exposed, who owns it, and how to remediate without creating an outage.

Most organisations have pieces of this information, but they live in separate systems:
- Cloud and infrastructure inventory.
- CMDB and service catalogue.
- Endpoint and vulnerability scanners.
- Container registries and Kubernetes clusters.
- SBOM and software composition analysis tools.
- Source control and CI/CD.
- ITSM, change management and incident response.
- Business criticality and data classification.

The key failure mode is not necessarily lack of a scanner. It is lack of reliable correlation and end-to-end closure.

## Why the problem becomes large

Consider one critical library or runtime used by many applications. It may appear in:
- VM-installed packages.
- Container base images.
- Application dependencies.
- Build agents and CI runners.
- Serverless deployment bundles.
- Managed platform runtimes.
- Development, test, staging, production and disaster-recovery environments.

A single advisory can therefore generate many findings, duplicate tickets and conflicting remediation instructions. A version match alone may also create false positives where a vendor has backported a fix, or false confidence where the deployed runtime differs from the build-time inventory.

## Quantify the scale in your estate

Build a baseline using measured values rather than generic industry estimates.

| Dimension | Measurement |
|---|---|
| Estate size | Managed assets, workloads, clusters, repositories and images |
| Technology spread | Unique products, runtime versions and dependency versions |
| Exposure | Internet reachable, privileged, sensitive-data and lateral-movement paths |
| Ownership | Assets with valid service owner and support team |
| Detection | Time from advisory publication to asset correlation |
| Delivery | Time from assignment to deployed fix |
| Assurance | Percentage independently verified after deployment |
| Governance | Open exceptions, overdue exceptions and repeat findings |

## Illustrative sizing model

For planning, estimate the work queue as:

`Remediation demand = affected asset groups × remediation paths × validation effort`

Group identical assets by owner, platform, image digest and deployment pattern. This avoids treating every replica as a separate engineering project while preserving asset-level evidence.

Do not use this model as a claim about actual vulnerability counts. Populate it from CMDB, cloud inventory, scanners, registries and runtime telemetry.

## Business impact

Unmanaged exposure can create:
- Remote compromise or service disruption.
- Data confidentiality and integrity impact.
- Lateral movement through shared infrastructure.
- Supply-chain compromise through build systems and dependencies.
- Regulatory, contractual and audit exposure.
- Unplanned downtime from emergency patching.
- Engineering capacity loss through duplicate triage and manual reconciliation.

The architecture must reduce both security exposure and the operational cost of responding to it.
