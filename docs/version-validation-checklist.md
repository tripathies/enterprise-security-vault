# Version and validation checklist

Use this checklist for each discovered instance. Fixed-version values must be refreshed from the current official vendor advisory before a change is approved.

| Technology | Discover | Validate | Remediate | Verify |
|---|---|---|---|---|
| PHP | CLI, PHP-FPM, package and container runtime | Branch, package revision and vendor fixed release | Upgrade runtime/package and restart relevant service | Check CLI and web runtime; health check |
| GitLab Self-Managed | Instance version and deployment type | GitLab advisory and supported upgrade path | Backup and follow required upgrade sequence | Confirm GitLab version, health and background migrations |
| Node.js | Runtime on hosts, containers, build agents | Actual runtime and image digest | Update runtime/dependency image and redeploy | Check running process/container version and app health |
| NGINX | Package/build, modules and config | F5/vendor/distribution advisory applicability | Apply package/configuration fix | Run config test, reload safely and verify running package/service |

## Useful discovery commands

### PHP
```bash
php -v
php --ini
systemctl list-units --type=service | grep -i php
```

CLI output alone does not prove which PHP-FPM version serves web traffic.

### GitLab Self-Managed
```bash
sudo gitlab-rake gitlab:env:info
sudo gitlab-ctl status
```

Follow the official GitLab upgrade path; do not skip required upgrade stops.

### Node.js
```bash
node -v
npm -v
```

Also inspect container images, deployed workloads and build agents.

### NGINX
```bash
nginx -v
nginx -V
sudo nginx -t
```

Use distribution package metadata and vendor advisory guidance because package maintainers may backport security fixes.

## Closure evidence

- Asset/service identity.
- Advisory reference and assessment.
- Before and after package/runtime version.
- Image digest or deployment revision where relevant.
- NGINX configuration validation where applicable.
- Change/ticket reference.
- Service health and post-change scan.
- Timestamp and responsible team.
