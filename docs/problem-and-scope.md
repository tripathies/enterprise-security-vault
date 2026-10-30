# Problem and scope

## Problem statement

Security advisories have been issued for four technologies: **PHP, GitLab, Node.js and NGINX**.

An organisation may use these components in applications, servers, containers, build systems and self-managed platforms. The immediate challenge is to identify every relevant installation, determine whether it is affected, upgrade it safely and prove that the running environment is fixed.

## Why it matters

A single technology may be deployed in multiple environments and maintained by different teams. Manual checking can miss:
- A PHP-FPM runtime that differs from the CLI version.
- A self-managed GitLab instance maintained separately from GitLab.com.
- Node.js bundled inside an application container or used by a build agent.
- NGINX instances with configuration or modules relevant to a specific advisory.
- Old images or dormant environments that are still deployable or exposed.

## Scope

This project covers only:
1. PHP
2. GitLab Self-Managed
3. Node.js
4. NGINX

It does not attempt to solve every vulnerability-management problem or create a generic enterprise security platform.

## Success

For these four technologies, the organisation can answer:
- Where is each component running?
- Which vendor advisory applies?
- Which instances need an upgrade or configuration change?
- Who owns the remediation?
- Has the running deployment been verified after the change?
