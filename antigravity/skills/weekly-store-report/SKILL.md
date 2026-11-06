---
name: weekly-store-report
description: Write a weekly report on one AI app store. Use when the user asks for a weekly summary, digest or report of a store, such as its top movers, launches, featuring and listing changes.
---

Use this skill when the user wants one store's week in a single report. The user's own instructions come first.

## Flow

1. `stores_get` with `store` and `guide=weekly_brief` returns the steps of a weekly brief for that store and its chart names.
2. `charts_get` on the store's lead chart gives the current order with each app's movement.
3. `changes_list` with `since=-7d` gives the week's events with counts per type: rank moves, chart entries and exits, featuring, launches, listing edits and delistings.
4. `new_list` with `since=-7d` lists the week's launches.
5. `featuring_history` with `since=-7d` lists the apps featured on the store's home page.

## The report

- Headline: the two or three moves that matter most this week.
- Sections: top of the chart, biggest climbers and fallers, new launches, featuring, listing changes.
- Each line gives the app, the change and its date, linked to the app's theopenapps.com page; the report states the date range it covers.

## Scope

- A chart position is a store rank, not a download count. OpenApps publishes no estimates of installs, users or revenue.
- Signed out, the report covers United States charts and the top 200 rows of each list.
