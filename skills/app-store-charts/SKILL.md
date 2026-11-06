---
name: app-store-charts
description: Read AI app store charts with OpenApps. Use when the user asks which apps lead the ChatGPT, Claude, Cursor, Grok Bot, Perplexity or Muse store, a category chart, how apps moved, or what is popular over the last month.
---

Use this skill when the user wants to know what ranks where in the app stores inside AI assistants. The user's own instructions come first.

## Flow

1. `stores_get` lists the stores OpenApps covers, with each store's app count, countries, charts, kinds and metrics. With `store`, it returns that store's chart names, such as `category:productivity` on ChatGPT or `popularity` on Claude.
2. `charts_get` returns one chart now, or at a past time with `at`: each app's 1-based position, its previous position and whether it is new to the chart. ChatGPT charts are per country (`region`, default `us`); each other store has one catalog.
3. `scores_list` ranks a store's apps by OpenApps Rank, a 28-day aggregate of the store's popularity charts, with tier and momentum. `leaderboards_get` ranks apps by a number the store publishes, such as installs on Claude or directory installs on Cursor.
4. `market_get` gives each store's size, app kinds and launches per week.
5. `stores_get` with `guide=weekly_brief` returns the steps of a weekly brief for one store.

## Reading the answers

- Answers are text: a header with the date the data refers to, CSV rows, then lines for paging (`next_cursor`), coverage and anything left out of a signed-out answer.
- Each row links to the app's page on theopenapps.com; answers that cite those links let the user check them.
- A chart position is a store rank, not a download count. OpenApps publishes no estimates of installs, users or revenue.
- Signed out, answers cover the United States and the top 200 rows of a list. A linked OpenApps account opens the other countries and more rows.
