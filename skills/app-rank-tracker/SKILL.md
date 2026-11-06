---
name: app-rank-tracker
description: Track your own app across the AI app stores after launch. Use when the user says "my app", "our app", "where do we rank", "track my app" or names their own app or publisher and wants its ranks, rank changes, featuring or listing changes.
---

Use this skill when the user follows their own app, or their company's apps, after launch. The user's own instructions come first.

## Flow

1. Without an app name or publisher in the conversation, the first step is to ask for one.
2. `listings_search` finds the app's listings: `query` with the app's name, or `publisher` with the company name to list all of its apps. Each row has a listing ref (`{store}:{plugin_id}`).
3. `listings_profile` with the ref gives the listing's place in every chart it is in now, its previous position, the metrics its store publishes and its MCP tools. Signed out, a profile covers one listing per call, so an app in three stores takes three calls.
4. `changes_list` with `apps` set to the ref and `since=-7d` lists the week's events for it: rank moves, chart entries and exits, featuring, listing edits and MCP tool changes.
5. `featuring_history` with `app` set to the ref shows when and where the store featured it.

## The answer

- One block per store: the best chart place now, the change over the week, any featuring, and the listing edits seen, each with dates.
- Links to the app's theopenapps.com pages, where the rank history is charted.
- When the app isn't found: the name as searched, the closest matches, and that a listing shows up in OpenApps once its store lists it.

## Scope

- A chart position is a store rank, not a download count. OpenApps publishes no estimates of installs, users or revenue.
- Signed out, changes and featuring go back 7 days and answers cover United States charts. A linked OpenApps account opens longer history and the other countries.
