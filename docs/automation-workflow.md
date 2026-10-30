# Automation workflow — four technology security response

## Goal

Automate the repetitive work for PHP, GitLab, Node.js and NGINX: discovery, version comparison, ticket creation, approved remediation and verification.

## Workflow

1. Run on a schedule and when a new relevant advisory is added.
2. Query approved host, cloud, container and platform inventories.
3. Discover PHP, GitLab Self-Managed, Node.js and NGINX instances.
4. Collect version, asset ID, environment, owner and last-seen time.
5. For NGINX, collect relevant package/build, module and configuration evidence.
6. Compare each instance against the current vendor advisory and fixed release guidance.
7. Mark each record as `affected`, `not_affected`, `needs_review` or `unknown`.
8. Group findings by service/owner and create or update remediation tickets.
9. Route approved changes to the existing patching or CI/CD process.
10. Verify the deployed runtime/package/configuration and service health.
11. Close only when the evidence passes; otherwise reopen or escalate.

## Suggested automation components

| Function | Possible implementation |
|---|---|
| Scheduling | GitHub Actions schedule, enterprise scheduler or cloud event service |
| Inventory | CMDB, cloud inventory, endpoint management, Kubernetes and registry APIs |
| Discovery | Approved remote inventory agents and platform APIs |
| Advisory data | Maintained vendor advisory records and security feeds |
| Comparison | Version-aware rules with package-specific backport handling |
| Workflow | Existing ITSM API |
| Execution | Existing patch management, configuration management or CI/CD |
| Verification | Runtime/package query, configuration test, service health and post-patch scan |
| Reporting | CSV/JSON output and security dashboard |

These are implementation options, not a requirement to deploy every product.

## Safe automation rules

- Discovery and reporting may run automatically.
- Production patching must follow the organisation's change policy.
- Test the upgrade in a lower environment first.
- Use least-privilege credentials and short-lived identity.
- Make jobs idempotent; repeated runs must not create duplicate tickets or repeat unsafe changes.
- Record source advisory, asset, before/after version, operator/workflow, change ID, timestamp and validation result.
- Define rollback or mitigation before production execution.
- Do not treat unknown inventory or failed discovery as not affected.

## Example output record

```json
{
  "technology": "Node.js",
  "asset_id": "service-prod-001",
  "environment": "production",
  "observed_version": "REPLACE_WITH_DISCOVERED_VERSION",
  "advisory_id": "REPLACE_WITH_VENDOR_ADVISORY",
  "assessment": "needs_review",
  "owner": "platform-team",
  "ticket": null,
  "verification": "pending",
  "last_seen_utc": "REPLACE_WITH_TIMESTAMP"
}
```

This is a schema example, not a real finding. Populate advisory IDs and fixed versions from current official vendor records.
