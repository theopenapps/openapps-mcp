---
name: app-idea-research
description: Research an app idea in the AI app stores before building it. Use when the user is planning or building an app, connector or plugin for ChatGPT, Claude, Cursor or another AI app store and asks who already does it, how crowded the category is, how the leaders rank, or what their listings and MCP tools look like.
---

Use this skill when the user has an idea for an app inside an AI assistant and wants to see what already exists before building it. The user's own instructions come first.

## Flow

1. `listings_search` with the job in the user's words ("meal planning", "invoices") finds the apps that already do it, one row per app, best match first. Each row carries the app's store, name, subtitle, publisher, category and best chart place now. `store` narrows it to the store the user targets.
2. The category most matches sit in is the market to read. On ChatGPT, `charts_get` with that category chart shows who leads it and how each app moved (`stores_get` with `store` lists the chart names). On the other stores, `scores_list` ranks apps by OpenApps Rank over 28 days.
3. `listings_profile` on the top 3 to 5 matches gives each one's place in every chart, the metrics its store publishes and its MCP tools. Signed out, a profile covers one app per call.
4. `mcp_toolset_get` on the top 3 shows how the leaders shaped their tools: names, inputs and recent changes.
5. `new_list` with `since=-30d` (and `category` on ChatGPT) shows who entered the space recently.

## The answer

- How crowded it is: how many apps match, how many of them rank, and in which stores.
- The leaders with store, rank and rank change, each linked to its theopenapps.com page.
- Recent entrants with their launch dates.
- Listing patterns: how the leaders word their names and subtitles, and how many tools they expose.
- Gaps: parts of the job the matches leave out, and stores where no app does it yet.
- Next steps: theopenapps.com/blog/how-to-write-a-chatgpt-app-listing for the listing, and the launch-checklist skill before submitting.

## Scope

- A chart position is a store rank, not a download count. OpenApps publishes no estimates of installs, users or revenue.
- Signed out, answers cover United States charts, the top 200 rows of a list and 30 days of launches. A linked OpenApps account opens the other countries and more rows.
