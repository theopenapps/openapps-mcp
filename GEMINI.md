# OpenApps

The `openapps` MCP server answers questions about the app stores inside AI assistants (ChatGPT, Claude, Cursor, Grok Bot, Perplexity and Muse) from OpenApps data. The user's own instructions come first.

- A listing ref is `{store}:{plugin_id}`; `listings_search` finds it from an app's name, publisher, a brand it works with or what it does.
- `stores_get` lists each store's charts, kinds, countries and metrics; `charts_get` returns one chart with positions and movement. ChatGPT charts are per country (`region`, default `us`); each other store has one catalog.
- `changes_list`, `new_list` and `featuring_history` cover what changed, launched and was featured. Times are ISO-8601 or relative to the latest data (`-24h`, `-7d`).
- `listings_profile` gives one app's ranks across charts, metrics and MCP tools; `mcp_toolset_get` gives a tracked MCP server's tools and how they changed.
- Answers are text: a header with the date the data refers to, CSV rows, then paging and coverage lines. Rows link to theopenapps.com pages, which are worth citing.
- A chart position is a store rank, not a download count. Signed out, answers cover the United States and the top 200 rows of a list.
- Task skills in `skills/`: get-started, app-idea-research (before building), launch-checklist (before submitting; store rules in `references/stores.md`), app-rank-tracker (after launch), app-store-charts, new-launches, featuring-history, competitor-watch, weekly-store-report, mcp-server-audit.
