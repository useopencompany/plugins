# Google Admin

An opencompany-hosted MCP adapter for Google's official Admin SDK Directory API.
This is maintained by opencompany, not a Google-hosted remote MCP server.

Install in opencompany under Settings → Plugins → Google Admin, then connect a
Google Workspace administrator with user and group management privileges.
Personal Gmail accounts cannot administer a Workspace directory.

Directory reads and all changes default to **Ask**. Review discovered tool schemas
before execution. Unclassified tools also require confirmation. OAuth credentials
stay server-side; the MCP endpoint accepts only short-lived operation tickets.

Tools list/get/create users, list/get/create/edit group details, list direct group
members, and add members with MEMBER, MANAGER, or OWNER roles. Groups inherit
Google's default access policies; review posting and visibility in Google Admin.

User creation generates and discards a random initial password. An administrator
must reset the password and send sign-in details securely through Google Admin.
No invitation is sent. Google may assign licenses based on the customer's settings.
There are no deletion, suspension, password-reset, super-admin, member-removal,
or group-policy tools. Inspect resources before retrying an uncertain write.

References reviewed 2026-09-10:
- https://developers.google.com/workspace/admin/directory/reference/rest
- https://developers.google.com/workspace/admin/directory/v1/guides/authorizing
- https://developers.google.com/workspace/admin/directory/v1/guides/manage-users
- https://developers.google.com/workspace/guides/configure-mcp-servers
