# Convex

Connect one Convex cloud deployment through opencompany's hosted bridge to the official
Convex CLI MCP server, pinned to `convex@1.45.0`. Install from Settings → Plugins → Convex,
then paste a deployment-scoped `dev:` or `prod:` deploy key from Convex deployment settings.
The key must permit function inspection so opencompany can validate the connection.
Project tokens, personal login credentials, preview-project keys, self-hosted endpoints,
and unscoped admin keys are not accepted.

Deployment metadata, schemas, and function specifications default to On. Documents,
read-only queries, and logs default to Ask. Running a function defaults to Ask because
it may execute a mutation or an action with external effects. Environment-variable
access and changes default to Off. Unknown tools require confirmation.

Production deployments expose only metadata, schemas, and function specifications.
Changing a permission to On does not relax this restriction. Development deployments
can use the other tools within the key's Convex permissions. The insights tool is
unavailable with deploy-key authentication and is omitted.

The bridge supplies deployment selection: tools do not accept project directories or
Convex deployment selectors. The deploy key is encrypted server-side and supplied only
to the pinned official CLI. The package contains no credentials or executable code.
The endpoint requires a short-lived opencompany gateway ticket and cannot be used as
an unauthenticated public Convex MCP server.

Reviewed metadata: live `tools/list` from `convex@1.45.0`, September 9, 2026.
Source: https://docs.convex.dev/ai/convex-mcp-server
