---
name: mcp-server-audit
description: Study the MCP servers behind AI app store listings with OpenApps. Use when the user asks which tools an app's MCP server exposes, how its toolset changed, or how a server's tools compare with other open servers.
---

Use this skill when the user studies MCP tool design or follows a server's tools. The user's own instructions come first.

## Flow

1. `mcp_toolset_get` returns a tracked server's stored tools, by app ref or server URL. `at` selects a past snapshot; `diff_from` (for example `-30d`) lists the tools added, removed and changed since an earlier version.
2. `listings_profile` shows which MCP servers an app links to, with their latest tools.
3. `market_get` gives MCP ecosystem statistics: open servers, tool counts and the most common parameters.
4. `stores_get` with `guide=audit_my_server` returns the steps for reviewing a server's tools against the open servers.

## Scope

- OpenApps tracks the MCP servers that store listings link to; an arbitrary URL that no listing links to has no stored toolset.
- A server that needs a sign-in shows no toolset. That is expected and doesn't mean the server is broken.
- Each answer gives the date its toolset was seen and links to the app's page on theopenapps.com.
