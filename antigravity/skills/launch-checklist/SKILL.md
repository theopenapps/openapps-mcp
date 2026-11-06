---
name: launch-checklist
description: Check a store's listing rules and the category's listings before submitting an app. Use when the user is about to submit or publish an app, connector or plugin to ChatGPT, Claude, Cursor or Grok Bot and asks what the store requires or how top apps word their listings.
---

Use this skill when the user is getting an app ready for an AI app store's review. The user's own instructions come first.

OpenApps reads store data; the user submits in each store's own portal. When the user asks for the submission itself, the answer gives the store's steps from `references/stores.md` and the portal link, and leaves the submitting to the user.

## Flow

1. `references/stores.md` holds each store's requirements as of 2026-11: where to submit, account, sign-in options, listing fields and their limits, review material, review times and policy limits.
2. `listings_search` with the app's job, plus `store`, finds the apps the new listing will sit next to.
3. `listings_profile` on the top 3 in that category (one per call signed out) shows their ranks, and the search rows show their names, subtitles and categories, so the answer can point at wording patterns that rank.

## The answer

- A checklist for the chosen store: each required field with its limit, the review material (test cases, demo video, reviewer account), and the policy points that most often block review.
- Two or three wording patterns from the category's top listings, with links to their theopenapps.com pages.
- The store's guide on theopenapps.com:
  - ChatGPT: theopenapps.com/blog/how-to-submit-a-chatgpt-app and theopenapps.com/blog/chatgpt-app-launch-checklist
  - Claude: theopenapps.com/blog/how-to-submit-a-claude-plugin-or-connector
  - Cursor: theopenapps.com/blog/how-to-publish-a-cursor-plugin
  - Grok Bot: theopenapps.com/blog/how-to-get-a-plugin-into-grok-bot
- After launch, the app-rank-tracker skill follows the app's ranks.

## Scope

Store rules change; `references/stores.md` gives the date they were read, and each store's own documentation is the final word.
