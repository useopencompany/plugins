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

## Events

The package declares one webhook event, `function.failed`, which fires when a function in the
connected deployment fails. opencompany creates a Convex webhook log stream for the deployment
with the deploy key already stored for this plugin, subscribed to the `verification` and
`function_execution` topics only, and verifies every delivery's HMAC-SHA256 signature. Log
streams require a Convex Pro plan, and the deploy key needs `deployment:integrations:write`.

Repeat failures of the same function with the same error are grouped, so a function failing
continuously starts one workflow run per grouping window rather than one per failed execution.
The optional `function_type` filter narrows a trigger to queries, mutations, actions, or HTTP
actions.

The bridge supplies deployment selection: tools do not accept project directories or
Convex deployment selectors. The deploy key is encrypted server-side and supplied only
to the pinned official CLI. The package contains no credentials or executable code.
The endpoint requires a short-lived opencompany gateway ticket and cannot be used as
an unauthenticated public Convex MCP server.

Reviewed metadata: live `tools/list` from `convex@1.45.0`, September 9, 2026.
Source: https://docs.convex.dev/ai/convex-mcp-server
Event source: https://docs.convex.dev/production/integrations/log-streams/
