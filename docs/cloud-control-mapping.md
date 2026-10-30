# Where to discover the four technologies

This repository is limited to PHP, GitLab Self-Managed, Node.js and NGINX. Discovery mechanisms depend on where each component runs.

| Location | PHP | GitLab | Node.js | NGINX |
|---|---|---|---|---|
| Linux VM | Package manager, CLI and PHP-FPM inventory | GitLab package/version and service inventory | Runtime manager, process and package inventory | Package manager, build flags and service inventory |
| Container | Image SBOM, package scan and running process | GitLab container/deployment version where applicable | Image SBOM and runtime process | Image package/build, modules and mounted configuration |
| Kubernetes | Pod image and runtime evidence | Self-managed GitLab workload/version | Pod image and runtime evidence | Ingress/controller image, modules and configuration |
| CI/CD runner | Build image/package inventory | Runner version and executor image | Runner runtime and build image | Build/test image if included |

Cloud-native inventory and security services may help identify the underlying VM, cluster, registry or workload, but they do not replace technology-specific version and configuration checks.

Use the organisation's existing AWS, Azure, GCP or OCI inventory and execution tools. Do not introduce a separate product for every cloud unless a demonstrated gap requires it.