<p align="center"><img src="assets/logo.svg" alt="OpenApps" width="96" height="96"></p>

# OpenApps MCP server

[OpenApps](https://theopenapps.com) is market intelligence for the app stores inside AI assistants. Its MCP server answers questions about what is listed, ranked, featured and launched in the ChatGPT, Claude, Cursor, Grok Bot, Perplexity and Muse app stores, and which tools their apps' MCP servers expose. Answers use OpenApps data, give the date it refers to and link to each app's page on theopenapps.com.

Use it to research an app idea before you build it, check a store's rules before you submit, and track your own app's ranks, featuring and listing changes after launch.

The server is hosted by The Open Apps, Inc.; there is nothing to install or build. This repository holds its listing files for app stores, marketplaces and registries.

- Transport: Streamable HTTP
- Auth: none needed. Signing in to an OpenApps account with OAuth 2.1 (scope `catalog:read`) is optional.
- Docs: https://theopenapps.com/docs/mcp

## Connect

Each store listing has its own address; every address serves the same OpenApps data.

| Client | MCP URL |
|---|---|
| ChatGPT (plugin directory) | `https://theopenapps.com/mcp/chatgpt` |
| Claude (connectors directory: claude.ai, Desktop, Claude Code) | `https://theopenapps.com/mcp/claude` |
| Cursor and Grok Bot (Cursor Marketplace) | `https://theopenapps.com/mcp/cursor` |
| Microsoft 365 Copilot | `https://theopenapps.com/mcp/copilot` |
| Gemini (Google Connected Apps) | `https://theopenapps.com/mcp/gemini` |
| Perplexity | `https://theopenapps.com/mcp/perplexity` |
| Muse | `https://theopenapps.com/mcp/muse` |
| Directories and IDE marketplaces (Gemini CLI, Antigravity, Devin, LobeHub, Raycast, Cline, Docker) | `https://theopenapps.com/mcp/directory` |
| Any other MCP client, and the official MCP Registry entry | `https://theopenapps.com/mcp` |

Claude Code:

```sh
claude mcp add --transport http --scope user openapps https://theopenapps.com/mcp
```

Codex:

```sh
codex mcp add openapps --url https://theopenapps.com/mcp
```

Gemini CLI:

```sh
gemini extensions install https://github.com/theopenapps/openapps-mcp
```

Cursor (`~/.cursor/mcp.json`), VS Code (`.vscode/mcp.json` uses `"servers"` and `"type": "http"`) and most other clients:

```json
{
  "mcpServers": {
    "openapps": {
      "url": "https://theopenapps.com/mcp"
    }
  }
}
```

More clients: https://theopenapps.com/connect

## Tools

| Tool | What it does |
|---|---|
| `changes_list` | What changed in a store: chart moves, featuring, launches, listing edits, delistings, metric moves and MCP changes, newest first. |
| `new_list` | Apps launched in a store since a time, by launch date. |
| `stores_get` | The stores, with each one's countries, charts, kinds and metrics; on request, the steps of a playbook. |
| `charts_get` | One store chart now or at a past time, with 1-based positions and movement. |
| `leaderboards_get` | A store's apps ranked by a number the store publishes, such as installs. |
| `scores_list` | A store's apps by OpenApps Rank, a 28-day aggregate of its popularity charts, with tier and momentum. |
| `listings_search` | Find an app's listings by name, publisher, a brand it works with or what it does. |
| `featuring_history` | When and where apps were featured on a store's home page. |
| `listings_profile` | One listing: country availability, its place in every chart, published metrics and MCP tools. |
| `mcp_toolset_get` | A tracked MCP server's tools at a time, or what changed between two versions. |
| `market_get` | Store sizes, weekly launches, app kinds and MCP ecosystem statistics. |
| `search` | Search OpenApps for listings, apps, tags, charts and MCP servers (ChatGPT and Microsoft 365 Copilot addresses only). |
| `fetch` | One OpenApps document for an id from `search` (ChatGPT and Microsoft 365 Copilot addresses only). |
| `feedback_send` | Send the OpenApps team a report about a problem with OpenApps; the one tool that writes. |

What each tool changes: the read tools change nothing; they read OpenApps data. `feedback_send` stores one report for the OpenApps team, sent when the user asks for it or agrees to it, and changes nothing else.

Prompts: `weekly_brief` (a store's week), `competitor_watch` (compare apps), `audit_my_server` (review an MCP server's tools against the open servers).

## Skills

`skills/` holds ten task skills (Agent Skills format: `skills/<name>/SKILL.md`), read by Cursor, Grok Bot, Claude Code, Antigravity and Gemini CLI, and shipped in the ChatGPT plugin package.

| Skill | For |
|---|---|
| `get-started` | What OpenApps covers and the three common jobs (ChatGPT's onboarding skill) |
| `app-idea-research` | Who already does an app idea, how crowded it is, how the leaders rank and shape their tools |
| `app-rank-tracker` | Your own app's ranks, rank changes, featuring and listing edits in every store |
| `launch-checklist` | A store's listing rules (`references/stores.md`, as of 2026-11) and how the category's top apps word their listings |
| `app-store-charts` | Top charts and rank changes by store |
| `new-launches` | Apps launched in a store this week or month, by category |
| `featuring-history` | Which apps a store featured on its home page, where and for how long |
| `competitor-watch` | Launches, changes and featuring for the apps you follow |
| `weekly-store-report` | One store's week: top movers, launches, featuring and listing changes |
| `mcp-server-audit` | An MCP server's tools and how they changed |

## Example prompts

- Use OpenApps to show the top Productivity apps in the ChatGPT app store, with rank changes.
- Use OpenApps to list the Claude connectors launched this week.
- Use OpenApps to show what changed in the Cursor marketplace in the last 7 days.
- Use OpenApps to find an app's listings across the AI app stores and show where it ranks.
- Use OpenApps to research my app idea, an invoice connector for Claude: which apps already do this, and how crowded is it?
- Use OpenApps to show where my app ranks in each AI app store this week.
- Use OpenApps to show which tools an app's MCP server exposes and what changed in them this month.
- Use OpenApps to compare how many apps each AI app store lists and how many launch each week.

## What works without an account

United States charts, the top 200 rows of each list, one listing per `listings_profile` call, 30 days of launches and 7 days of rank, change and featuring history, at 60 requests a minute. An OpenApps account adds every country (ChatGPT charts cover 48) and 1,000 rows; Pro adds every row and the full history. Plans: https://theopenapps.com/pricing

A chart position is a store rank, not a download count; OpenApps doesn't estimate installs, users or revenue.

## Files in this repository

| File | For |
|---|---|
| `.cursor-plugin/plugin.json`, `.grok-plugin/plugin.json` (the same file), `mcp.json`, `.mcp.json` | Cursor Marketplace and Grok Bot (`/mcp/cursor`); cursor.directory |
| `skills/` | Ten task skills (above) for Cursor, Grok Bot, Claude Code, Antigravity and Gemini CLI |
| `gemini-extension.json`, `GEMINI.md` | Gemini CLI extensions gallery (`/mcp/directory`) |
| `antigravity/` | Antigravity Marketplace (`/mcp/directory`) |
| `devin/` | The Devin marketplace entry, as added to CognitionAI/devin-marketplace (`/mcp/directory`) |
| `lhm.plugin.json` | LobeHub MCP marketplace (`/mcp/directory`) |
| `server.json` | Official MCP Registry entry `com.theopenapps/openapps` (`/mcp`; a copy of the server's own `server.json`) |
| `assets/logo.svg`, `assets/logo.png` | Logo (512 × 512 PNG) |

## Data

Tool inputs are store names, chart names, listing refs, dates and paging cursors; no tool asks for a name, an email address or other personal details. The 11 read tools also take an optional `context`: the user's goal in a few words, at most 500 characters. OpenApps removes email addresses, URLs and long numbers from it, cuts it to 300 characters and sends it to PostHog with the call's usage event for product analytics, as the [privacy policy](https://theopenapps.com/legal/privacy) says.

## Privacy, terms and support

- Privacy policy: https://theopenapps.com/legal/privacy
- Terms of service: https://theopenapps.com/legal/terms
- Support: https://theopenapps.com/support · hello@theopenapps.com

## Related

- [Plugin Stack](https://github.com/theopenapps/plugin-stack): agent skills for getting your own ChatGPT app, Claude connector or Cursor plugin into the stores, found and picked. They read the same OpenApps data.

## License

The files in this repository are MIT licensed ([LICENSE](LICENSE)). The OpenApps service and its data are covered by the [terms of service](https://theopenapps.com/legal/terms). The OpenApps name and logo are trademarks of The Open Apps, Inc. and are not licensed under MIT.
