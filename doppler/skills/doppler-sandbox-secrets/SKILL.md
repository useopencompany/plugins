---
name: doppler-sandbox-secrets
description: Use Doppler in coding sandboxes to set up worktrees, run existing development scripts with injected secrets, and perform explicitly requested secret changes.
---

Doppler is preinstalled in opencompany sandboxes. When the user's Doppler plugin is connected,
opencompany restores that user's CLI authentication. If authentication is unavailable, ask them to
connect or reconnect in Settings → Plugins → Doppler; never request credentials in chat.

Read the repository setup instructions and Doppler YAML. Run `doppler setup --no-interactive` in
each new worktree before its development scripts. Directory mappings belong to each worktree;
do not replace them with a global project, config, or single-config service token.
Keep existing scripts such as `pnpm dev` that invoke `doppler run -- ...` unchanged.

Prefer `doppler run -- <command>` to inject secrets directly into the process that needs them.
Never print tokens, secret values, CLI config files, or fallback caches. Validate configuration by
reporting missing names or pass/fail results without values. If a tool requires a secrets file,
redirect CLI output into an ignored file created with `umask 077`, and never display its contents.

The CLI inherits the connected account's Doppler permissions. Plugin tool permission switches do
not govern arbitrary terminal commands. A request to run the app does not authorize secret changes.
Create, update, or delete secrets only when explicitly requested and after resolving the exact
project/config and secret names. Reuse protected input files for secret values; do not put them in
shell arguments or transcripts. Use Doppler's current CLI help for the relevant operation.
