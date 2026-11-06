---
name: featuring-history
description: See which apps a store featured on its home page, where and for how long. Use when the user asks who got featured, what is on a store's home shelves, or how long an app stayed featured.
---

Use this skill when the user asks about the apps a store puts on its home page. The user's own instructions come first.

## Flow

1. `stores_get` with `store` lists the store's charts, including its home shelves (for example `home:featured` or `home:productivity` on ChatGPT).
2. `featuring_history` gives featuring intervals over up to 30 days: per shelf with `chart`, or per app with `app` (a listing ref from `listings_search`). `since` sets the window (`-7d`, `-30d`); `region` picks the ChatGPT country.
3. `charts_get` on the featured apps' category charts shows how their ranks moved while they were featured.

## The answer

- Each featured app with its shelf, start and end dates and days on the shelf, newest first.
- Rank moves during the featuring, when the user asks whether featuring helped.
- Links to each app's theopenapps.com page, and theopenapps.com/blog/how-to-get-on-a-chatgpt-home-shelf for how home shelves work.

## Scope

- Featuring is the store's own editorial choice; OpenApps records where and when, not why.
- Signed out, featuring history goes back 7 days and covers the United States. A linked OpenApps account opens up to 30 days and the other countries.
