---
name: competitor-watch
description: Follow apps in AI app stores with OpenApps. Use when the user asks what launched, changed or was featured in the ChatGPT, Claude, Cursor, Grok Bot, Perplexity or Muse store, or tracks named apps' ranks, listing edits and featuring.
---

Use this skill when the user follows a store or a set of apps over time. The user's own instructions come first.

## Flow

1. `listings_search` finds an app's ref (`{store}:{plugin_id}`) from its name, its publisher, a brand it works with or what it does, one row per app, best match first.
2. `listings_profile` shows one listing: its app, country availability, its position in every chart it is in, the metrics its store publishes and its MCP tools.
3. `changes_list` lists a store's events newest first, with counts per type: chart moves, entries and exits, featuring, launches, listing edits, delistings, metric moves and MCP changes. `apps` narrows it to the apps the user follows, `types` to some kinds of event, and `since` sets the window (24 hours by default; `-7d` for a week).
4. `new_list` lists the apps launched in a store since a time, by launch date.
5. `featuring_history` gives when and where apps were featured on a store's home page, per app or per shelf.
6. `stores_get` with `guide=competitor_watch` returns the steps of a side-by-side comparison of apps.

## Notes

- Times are ISO-8601 or relative to the latest data: `-24h`, `-7d`, `-2w`.
- Signed out, changes and featuring go back 7 days and launches 30 days, and a profile covers one app at a time. A linked OpenApps account opens longer history.
- Each row links to its page on theopenapps.com.
