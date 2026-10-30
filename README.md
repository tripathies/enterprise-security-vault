# PHP · GitLab · Node.js · NGINX Security Response

**Four technologies. One focused problem. One repeatable remediation workflow.**

This repository documents a practical response to the security advisories highlighted for **PHP, GitLab, Node.js and NGINX**. It is deliberately limited to these four technologies—not a generic enterprise vulnerability-management framework.

## 1. Problem statement

Security fixes have been released for PHP, GitLab, Node.js and NGINX. An organisation may be running one or more of these technologies across servers, applications, containers and self-managed platforms.

The immediate problem is simple:

**Do we know where these four technologies are running, which instances need attention, and whether the required fixes have actually been applied?**

Without a reliable inventory and repeatable patch process, teams may miss an instance, patch only a build image but not a running workload, overlook a self-managed GitLab installation, or fail to review an affected NGINX configuration.

## 2. What is in scope?

| Technology | What needs to be checked | Action |
|---|---|---|
| PHP | Runtime and PHP-FPM versions; supported branch; deployment packages | Upgrade to the applicable fixed release |
| GitLab | Self-managed instance version and release branch | Upgrade to the applicable GitLab security patch |
| Node.js | Runtime versions across hosts, containers and build/deploy environments | Upgrade to the applicable fixed release |
| NGINX | Installed package/build, enabled modules and affected configuration | Review F5 advisory K000163408 and apply the relevant vendor/distribution fix |

**Version note:** The versions shown in the original security infographic are the advisory's stated patch baselines, not a guarantee that they remain the newest releases. Always check the current vendor advisory and distribution security notice before deployment. Distribution packages may backport fixes.

## 3. Proposed solution

Create a small, focused **Four-Technology Security Remediation workflow**:

1. **Discover** — Find every PHP, GitLab, Node.js and NGINX installation.
2. **Inventory** — Capture host/container, environment, owner, installed version and deployment source.
3. **Compare** — Match each instance against the vendor's affected and fixed-version guidance; for NGINX, include configuration applicability.
4. **Prioritise** — Identify internet-facing and business-critical instances first.
5. **Remediate** — Create an owner-assigned change, patch or upgrade through the existing deployment process.
6. **Verify** — Recheck the running version/configuration and service health.
7. **Report** — Keep evidence of what was found, patched, deferred and verified.

## 4. How to automate it

A scheduled or event-triggered job can:

- Collect PHP, GitLab, Node.js and NGINX versions from approved inventory/management sources.
- Discover container images and running workloads that contain these components.
- Compare discovered versions with a maintained advisory data file.
- Flag unsupported, affected or unknown versions for review.
- Create or update one remediation ticket per affected service/asset group.
- Trigger an approved patch or rebuild pipeline after change approval.
- Run post-deployment checks and attach evidence.
- Reopen the ticket if the running instance remains affected.

**Do not blindly auto-patch production.** Use testing, maintenance windows, approvals, canary/rolling deployment and rollback controls appropriate to each service.

## 5. Repository contents

- [Four-technology problem and scope](docs/problem-and-scope.md)
- [Solution architecture](docs/solution-architecture.md)
- [Automation workflow](docs/automation-workflow.md)
- [Version and validation checklist](docs/version-validation-checklist.md)

## 6. Definition of done

The work is complete only when:
- Every known in-scope instance is accounted for.
- Each instance is matched to current vendor guidance.
- Required upgrades or mitigations are deployed.
- Running versions/configuration are rechecked.
- Application/service health is confirmed.
- Evidence and any approved exception are recorded.

**The objective is not to build a broad security platform. It is to make sure PHP, GitLab, Node.js and NGINX are found, assessed, fixed and verified—consistently.**
