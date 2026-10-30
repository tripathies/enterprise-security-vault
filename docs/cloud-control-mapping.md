# 5. Multi-cloud capability mapping

## Design principle

Use a common enterprise control model, but execute through the native capabilities already adopted in each platform. Product names are examples of capability mapping, not a requirement to purchase every service.

| Capability | AWS | Microsoft Azure | Google Cloud | Oracle Cloud Infrastructure |
|---|---|---|---|---|
| Asset inventory | AWS Config, Resource Explorer | Azure Resource Graph, Azure Resource Manager | Cloud Asset Inventory | OCI Cloud Guard / Search |
| Vulnerability findings | Amazon Inspector | Microsoft Defender for Cloud | Security Command Center | Vulnerability Scanning |
| Container/image security | ECR image scanning, Inspector | Defender for Containers, ACR scanning integrations | Artifact Analysis, Artifact Registry | Registry and image scanning integrations |
| Patch execution | Systems Manager Patch Manager | Azure Update Manager | OS Config / VM Manager capabilities | OS Management Hub |
| Security posture | Security Hub | Defender for Cloud | Security Command Center | Cloud Guard |
| Application edge protection | AWS WAF / Shield | Azure WAF / Front Door WAF | Cloud Armor | OCI WAF |
| Workflow integration | EventBridge, Lambda, Systems Manager | Event Grid, Logic Apps, Functions, Automation | Eventarc, Workflows, Cloud Run/Functions | Events, Functions, Notifications |
| Identity | IAM roles / STS | Managed identities / Entra ID | Workload Identity / IAM | Dynamic groups / resource principals |

Validate service availability, licensing, region support and current product naming against the provider documentation before implementation.

## Common control plane

Regardless of cloud:
1. Ingest findings and advisory context.
2. Normalise product, package, version and asset identifiers.
3. Correlate findings to service ownership.
4. Apply common risk policy.
5. Route work to ITSM and platform teams.
6. Invoke native remediation mechanism through approved integration.
7. Collect post-change evidence centrally.

## Avoid these anti-patterns

- Treating each cloud scanner as the complete enterprise inventory.
- Assuming scanner severity equals business risk.
- Running one generic patch script across unlike operating systems.
- Closing a finding because a pipeline succeeded.
- Ignoring images, build agents, dependencies and managed runtimes.
- Giving a central orchestrator broad standing administrator permissions.

The enterprise architecture should standardise policy, identity, evidence and workflow while preserving cloud-native execution.
