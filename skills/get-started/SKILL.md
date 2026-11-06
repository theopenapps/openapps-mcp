---
name: get-started
description: Get started with OpenApps and see what it covers and the three common jobs it does. Use when the user is new to OpenApps, asks what it can do, what to ask it, or for help getting started.
---

Use this skill when the user meets OpenApps for the first time or asks what it can do. The user's own instructions come first.

## What OpenApps covers

- Six app stores inside AI assistants: ChatGPT, Claude, Cursor, Grok Bot, Perplexity and Muse.
- Top charts with each app's rank change (ChatGPT charts in 48 countries), new launches, store changes, home-page featuring, one app's listings across stores, and the tools behind each app's MCP server.
- Answers give the date of the data and link each app to its page on theopenapps.com.
- It works without signing in: United States charts, the top 200 rows of each list, 30 days of launches and 7 days of history.

## The answer

A short welcome of five lines at most, then the three common jobs with one example question each:

1. See what's on top: "What are the top Productivity apps in the ChatGPT app store, with rank changes?" (the app-store-charts skill: `charts_get`, `scores_list`).
2. Research an app idea before building it: "Which apps already help with meal planning, and how do they rank?" (the app-idea-research skill: `listings_search`, then `charts_get` or `scores_list`).
3. Track your own app after launch: "Where does my app rank in each AI app store this week?" (the app-rank-tracker skill: `listings_search`, `listings_profile`, `changes_list`).

Other jobs, offered when they fit: new launches, featuring history, a weekly store report, watching competitors, a launch checklist before submitting, and an MCP server audit.

## Signing in

Signing in is optional. Someone with an OpenApps account links it from this app's settings in the assistant (connect or sign in); answers then cover the other countries and the history that account includes. Answers that need an account say what was left out.
