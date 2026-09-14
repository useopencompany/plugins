# Dash0

Connect a Dash0 organization through the official hosted MCP server. The package uses AWS Ireland as its bootstrap endpoint. opencompany follows Dash0’s explicit region-mismatch response to the reviewed AWS Ireland, AWS Germany, AWS Oregon, or GCP Netherlands endpoint. Other clients must support this regional routing or configure their organization’s endpoint. Authenticate with OAuth using the shared opencompany connection flow; no token belongs in this package.

Telemetry and investigation reads default to **Ask** because they can contain private operational data. `runTask` defaults to **Off**: it starts or continues paid Agent0 work and can access the network. Explicitly enable it only after reviewing Dash0 credit and network settings. Unreviewed or newly discovered tools require confirmation, including management tools.

Reviewed on 2026-09-14 against [Dash0 MCP setup](https://www.dash0.com/hub/integrations/int_dash0_mcp/overview), [Agent0 delegation documentation](https://www.dash0.com/docs/dash0/ai/agent0/overview/use-agent0/delegate-to-agent0), and the endpoint's live OAuth metadata. The nine named tools are documented by Dash0. Authenticated `tools/list` was unavailable during review (HTTP 401); this is not an exhaustive server inventory. The client must keep unmatched tools behind confirmation regardless of server annotations.

Regional routing was added after a real GCP Netherlands organization returned HTTP 421 (`organization_region_mismatch`). Existing opencompany installations recover on **Refresh** without reinstalling. OAuth refresh retains its original issuer; MCP routing uses a fixed endpoint allowlist and never an arbitrary URL or redirect. Regional base URLs are published in [Dash0’s API reference](https://www.dash0.com/docs/api-reference).
