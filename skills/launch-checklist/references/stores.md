# AI app store listing rules (as of 2026-11)

Read from each store's documentation and portal in early November 2026. Stores change their rules; each store's own documentation is the final word.

## ChatGPT plugin directory (OpenAI)

- **Where:** platform.openai.com/plugins → Upload new or existing plugin → With MCP. Apps were renamed plugins on 2026-07-09.
- **Package:** a ZIP with a root `plugin.json` (OpenAI fields under `extensions.com.openai`) and `mcp.json`, or `.codex-plugin/plugin.json`. One remote MCP server per plugin; one version in review at a time.
- **Account:** the owner of a verified OpenAI Platform organization (individual or business verification). The directory shows the verified name as the developer.
- **Sign-in:** none, or OAuth (a registered client, DCR or CIMD). API-key and bearer-token flows aren't available. A reviewer account, if sign-in is needed, has no MFA and needs no new sign-up step.
- **Domain proof:** a token served as plain text at `/.well-known/openai-apps-challenge` on the server's domain.
- **Tool scan:** `readOnlyHint`, `destructiveHint` and `openWorldHint` set on every tool.
- **Listing fields:** name ≤30 characters, subtitle ≤30, description ≤4,000, up to 3 starter prompts of ≤128, one category, square logo ≥48 px (≤5 MiB), website, support, privacy and terms URLs (https), keywords.
- **Search:** directory search matches the name, the subtitle, the keywords and the developer name word by word; the long description and prompts aren't searched.
- **Skills:** the listing page shows one row per `skills/<name>/` folder, labelled by `agents/openai.yaml` `display_name` and `icon_small`. `onboardingSkill` is the bare name of one of those skills, directly under `extensions.com.openai`.
- **Review material:** exactly 5 positive and 3 negative test cases, a demo video URL, release notes and the policy attestations.
- **Review:** an automated scan, then review, with feedback by email. Median 14.9 days from plugin id to live (OpenApps data, 2,966 plugins, Oct 11–24, 2026). After approval the developer presses Publish.
- **Policy points that block review:** no selling of digital goods inside the plugin and no links that send users to pay; listing copy names no costs or promotions; descriptions neither favour nor disparage other plugins; suitable for ages 13+; no reading or relaying third-party websites or services without authorization.
- Guides: theopenapps.com/blog/how-to-submit-a-chatgpt-app, theopenapps.com/blog/chatgpt-app-launch-checklist, theopenapps.com/blog/how-to-write-a-chatgpt-app-listing

## Claude connectors directory (Anthropic)

- **Where:** claude.ai/directory/manage → Submit new → MCP connector, by server URL. Listed in claude.ai, Claude Desktop, mobile and Claude Code.
- **Account:** a paid Claude account; on Team or Enterprise the organization's owner submits. The listing belongs to the submitting organization.
- **Sign-in:** none, OAuth with DCR, or OAuth with CIMD. "Required when the server asks": a protected call answers HTTP 401 with `WWW-Authenticate`, and Claude shows a Connect card.
- **Tools:** every tool has a `title` and `readOnlyHint` or `destructiveHint`. Results stay under about 150,000 characters.
- **Listing fields:** name ≤100 characters (no "Claude" or "Anthropic"), one-liner ≤200, description ≤2,000, 1–5 categories, documentation, privacy and support links, icon, and a URL slug that can't change after publishing.
- **Other steps:** use cases with example prompts, company and contact, data handling (own API, proxied with permission, or third party), reviewer test account and steps, confirmation that every tool was run, 7 compliance acknowledgments, public documentation by the publish date.
- **Screenshots:** only for MCP Apps (interactive cards): 3–5 PNG, at least 1,000 px wide.
- **Review:** an automated scan, then listed; some submissions also get a person's review. Escalations: mcp-review@anthropic.com.
- **Policy points that block review:** no money transfer, no AI image, video or audio generation, no advertising or sponsored content; the server calls the developer's own APIs or ones it may proxy, on a domain that matches the service.
- Guides: theopenapps.com/blog/how-to-submit-a-claude-plugin-or-connector, theopenapps.com/blog/how-to-write-a-claude-listing

## Cursor Marketplace and Grok Bot (one queue)

- **Where:** cursor.com/marketplace/publish (Cursor sign-in) or xAI's form at x.ai/bot/marketplace/submit-a-plugin. One accepted plugin appears in the Cursor Marketplace and in Grok Bot's Connect apps catalog. Submit once; changes go to marketplace-publishing@cursor.com.
- **Package:** a public GitHub repository holding `.cursor-plugin/plugin.json`, `mcp.json` (and `.mcp.json`), a logo, a README and a permissive license (no copyleft). A bare MCP URL also works, but the listing then shows Cursor as publisher.
- **Form fields:** name and work email (Gmail is rejected), organization name and handle, website, logo URL (square SVG or PNG on a solid plate), MCP URL or repository, description ≤600 characters, testing instructions ≤600, a "tested locally and in-app" box.
- **Check:** `grok plugin validate .` in the repository.
- **Review:** manual for every plugin and every update; no status page, and reasons aren't given.
- **Policy points:** the plugin charges users nothing through the marketplace; it collects only the data it needs and doesn't sell it.
- Guides: theopenapps.com/blog/how-to-publish-a-cursor-plugin, theopenapps.com/blog/how-to-write-a-cursor-plugin-listing, theopenapps.com/blog/how-to-get-a-plugin-into-grok-bot

## Grok Build plugin marketplace (xAI)

- **Where:** a pull request adding one entry to `.grok-plugin/marketplace.json` in github.com/xai-org/plugin-marketplace, pointing at a public repository pinned to a full commit SHA. MCP-only plugins are accepted.
- **Needs:** license, homepage, README, keywords and domains; a static security review.

## Every store

- One overview of all stores: theopenapps.com/blog/how-to-submit-an-app-to-ai-app-stores
