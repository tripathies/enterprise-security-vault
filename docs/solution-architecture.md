# Solution architecture — PHP, GitLab, Node.js and NGINX

## Objective

Provide one simple operational workflow to identify, assess, remediate and verify the four technologies named in the security roundup.

## Scope

- PHP runtimes, including PHP-FPM where deployed.
- GitLab Self-Managed instances.
- Node.js runtimes on hosts, in containers and in build/deployment environments.
- NGINX packages/builds, enabled modules and relevant configuration.

GitLab.com and vendor-managed services should be handled according to the provider's responsibility model; do not treat them as customer-managed servers.

## Logical flow

```mermaid
flowchart TD
 A[Approved asset sources] --> B[Discover PHP / GitLab / Node.js / NGINX]
 B --> C[Collect versions, locations, owners and environment]
 C --> D[Compare with current vendor advisories]
 D --> E{Affected or uncertain?}
 E -->|No| F[Record evidence and next scan]
 E -->|Yes| G[Prioritise by exposure and business criticality]
 G --> H[Create remediation ticket]
 H --> I[Approval and maintenance window]
 I --> J[Patch / upgrade / rebuild]
 J --> K[Verify running version and service health]
 K --> L{Pass?}
 L -->|Yes| M[Close with evidence]
 L -->|No| N[Rollback / investigate / escalate]
 N --> H
```

## Data to collect

| Field | Why it matters |
|---|---|
| Technology | PHP, GitLab, Node.js or NGINX |
| Asset/service ID | Stable identity for tracking |
| Host/container/image | Where the component runs |
| Environment | Development, test, staging, production |
| Owner/team | Who is accountable |
| Installed/runtime version | Version comparison |
| Package source | OS repository, vendor package, image, runtime manager |
| NGINX configuration/module facts | Needed to assess configuration-dependent exposure |
| Internet exposure | Helps order remediation |
| Last-seen timestamp | Avoids relying on stale inventory |
| Advisory/fixed-version reference | Traceability to vendor guidance |
| Ticket/change/evidence link | Audit and closure |

## Remediation paths

- **PHP:** Update the installed PHP package/runtime and relevant PHP-FPM service; confirm CLI and web-serving runtimes are aligned.
- **GitLab Self-Managed:** Follow GitLab's supported upgrade path and required intermediate upgrade stops; back up and validate before production changes.
- **Node.js:** Update the actual runtime used by the application, build agents and containers; rebuild and redeploy images where required.
- **NGINX:** Check the exact F5 advisory and distribution/vendor package guidance, enabled modules and affected configuration; validate configuration before reload/restart.

## Guardrails

- Never infer exposure from a product name alone.
- Check vendor and distribution backports before declaring a package vulnerable.
- Do not auto-disable production services based only on a version match.
- Use approved change windows and rollback plans.
- Confirm the running workload after deployment, not only the package repository or build pipeline.
