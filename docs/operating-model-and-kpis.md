# Ownership and measures — four-technology remediation

## Ownership

| Technology/work | Accountable team |
|---|---|
| PHP runtime and PHP-FPM | Application/platform owner |
| GitLab Self-Managed | GitLab platform administrator |
| Node.js runtime and images | Application/platform engineering |
| NGINX package, modules and configuration | Web/platform operations |
| Advisory applicability and risk | Security team |
| Change approval and service acceptance | Service owner / change authority |

## Measures

- **Inventory coverage:** known instances compared with expected deployment sources.
- **Unknown-version count:** instances whose version or configuration could not be established.
- **Time to identify:** advisory publication/intake to affected-instance list.
- **Time to assign:** confirmed finding to accountable owner.
- **Time to remediate:** confirmed finding to deployed fix or approved mitigation.
- **Verified closure:** findings with post-change version/configuration and health evidence.
- **Reopen rate:** findings that remain affected or recur after closure.

Report PHP, GitLab, Node.js and NGINX separately. Show the reporting window, source freshness and denominator. A ticket closure without running-state evidence is not verified remediation.