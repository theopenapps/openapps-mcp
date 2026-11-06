---
name: new-launches
description: See which apps just launched in an AI app store. Use when the user asks what's new, what launched this week or month, or which new apps entered a category.
---

Use this skill when the user asks about new apps in the ChatGPT, Claude, Cursor, Grok Bot, Perplexity or Muse store. The user's own instructions come first.

## Flow

1. `new_list` with `store` and `since` (`-7d` for a week, `-30d` for a month) lists the apps launched in the window, newest first, by launch date. `category` narrows it on ChatGPT; `kinds` narrows it on stores with several kinds (on Claude: connectors, plugins and desktop extensions; `stores_get` lists them).
2. `changes_list` with `types` set to `launch` and `chart_enter` and the same `since` shows which new apps already entered a chart.

## The answer

- How many apps launched in the window, then the newest grouped by category, each with its launch date, publisher and theopenapps.com link.
- The new apps that already entered a chart, with their position.

## Scope

- Signed out, launches go back 30 days and chart entries 7 days. A linked OpenApps account opens longer history.
