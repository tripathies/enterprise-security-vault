# Implementation plan — PHP, GitLab, Node.js and NGINX

## Phase 1 — Discover
Inventory PHP, GitLab Self-Managed, Node.js and NGINX across hosts, containers, build agents and environments. Record owner, environment, observed version and last-seen timestamp.

## Phase 2 — Assess
Compare observations with current official PHP, GitLab, Node.js and F5/NGINX advisories. Check supported branches, package backports and configuration applicability. Mark uncertain matches for manual review.

## Phase 3 — Prioritise
Order confirmed findings by vendor severity, internet exposure, business criticality and ease of safe remediation. Assign an accountable application or platform owner.

## Phase 4 — Remediate
Use the existing package manager, GitLab upgrade procedure, container build pipeline or NGINX package/configuration process. Test in a lower environment and follow change approval and rollback requirements.

## Phase 5 — Verify
Check the running version, deployed image or relevant NGINX configuration. Run service health checks and a post-change scan. Attach evidence to the remediation record.

## Completion criteria
Every known in-scope instance is accounted for; affected instances are patched or have an approved time-bound mitigation; and the deployed state is verified.