# opencompany plugins

Official [Agent Plugins 1.0.0](https://agent-plugins.org/) packages maintained by
[opencompany](https://opencompany.com).

Each top-level directory is a complete plugin package. Install one by giving any compatible
client the public GitHub URL for that directory. Production clients should pin the URL to a full
commit SHA so installation is reproducible and reviewable.

| Plugin | Package URL |
| --- | --- |
| Linear | `https://github.com/useopencompany/plugins/tree/main/linear` |

For example, clients that accept a source URL can install Linear from the package URL above. The
exact command or UI varies by client because Agent Plugins standardizes the package, not the
client's installation interface.

## Trust and contributions

Plugin packages can define executable capabilities. Treat every change as a supply-chain change:
open a pull request, review the complete package diff, and merge only after the required review.
Do not commit credentials or place credentials in plugin manifests, skills, or MCP configuration.

All packages are licensed under the [MIT License](LICENSE).
