---
name: threatcrush
description: Use the ThreatCrush MCP tools when the user asks about their security findings, vulnerabilities from threatcrush scan / pentest / ai-scan, security incidents on their servers, whether an IP address, domain or file hash is malicious, or their ThreatCrush webhooks. Also use when the user wants to triage, mark fixed or false-positive, or close out ThreatCrush findings and incidents.
---

# ThreatCrush

The `threatcrush` MCP server (https://threatcrush.com/api/mcp) exposes the user's
ThreatCrush account. The first tool call that needs an account prompts sign-in
(OAuth in the browser); run `/mcp` and choose threatcrush > Authenticate if it does not.

## When to use which tool

- "Is this IP / domain bad?", "who is attacking us?": `reputation_lookup` (one),
  `reputation_bulk` (many, e.g. from a log).
- "Is this file malware?": hash it locally with `sha256sum` and call `av_hash_lookup`.
  Send hashes only, never file contents. Works without signing in.
- "What vulnerabilities do we have?", "show open criticals": `findings_list`
  (filter by `severity`, `status`, `source`), then `findings_get` for details and
  remediation.
- "Mark these fixed / false positive": `findings_triage`. Fix the code first when
  you can, and put why in `note`.
- "What happened on dev2 last night?": `incidents_list` with `host` and an explicit
  `since` timestamp (include the timezone), then `incidents_get`.
- Recording fix work or closing an incident: `incidents_update`. Closing needs
  passing tests and verification plus `resolution.reason/action/verification`.
- Webhooks: `webhooks_*` (org admins only).

## Rules

- Read tools are safe to call freely. Before `findings_triage`, `incidents_update`,
  `webhooks_delete` or `webhooks_rotate_secret`, say what will change and confirm.
- `incidents_raise` pages humans by SMS and email: only raise when the user asks,
  and never for something already open (reuse the same `dedupe_key`).
- Users in several orgs: pass `org_id` when the answer could come from the wrong one.
- ThreatCrush catalogs and detects; it does not run remediation. Make the fix in the
  repo or on the server, then record it.
