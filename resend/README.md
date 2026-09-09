# Resend

Connect Resend through its [official hosted MCP server](https://resend.com/docs/mcp-server)
at `https://mcp.resend.com/mcp`. In opencompany, install Resend from Settings → Plugins,
then connect your account through Resend's OAuth consent screen. The connection requests
`full_access` to support the reviewed tool set; opencompany applies its own permissions
before dispatch. Credentials remain on the server and are bound to this exact endpoint.

| Capability | Default |
| --- | --- |
| Inspect email configuration | On |
| Read email and contact data | Ask |
| Send emails and manage content | Ask |
| Administer access and destructive actions | Off |

Email subjects, bodies, attachments, recipients, contact records, and request logs are
sensitive reads. Sending includes individual and batch messages, broadcasts, scheduling,
and automation triggers. Review recipients, sender, content, and timing before approving.
A verified sending domain is required for normal delivery, and completed sends cannot be undone.

API key administration, OAuth revocation, webhook configuration, domain ownership claims,
public email links, removing suppressions, and irreversible removals start Off.
`manage-events` can delete event definitions, so the entire tool starts Off, including
its list/get operations. `get-tiptap-json-content` also creates editor presence despite
its read-only annotation; it requires approval with the other content changes.

The hosted server cannot read files from your coding sandbox. For attachments and contact
imports, use content/base64 or a URL Resend can access instead of a local file path.

Reviewed on 2026-09-09 against all 103 tools returned by the hosted `tools/list` endpoint
and the [official source at 59d2380](https://github.com/resend/resend-mcp/tree/59d2380516e44f27ec07a9d2b6c148d2b98c62b6/src/tools).
New or unclassified tools require confirmation, even when they advertise read-only annotations.
