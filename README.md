# Awesome x402

A curated catalog of **HTTP 402** / **x402** rails for agent-native pay-per-request — especially **Base USDC**.

Inspired by how [public-apis](https://github.com/public-apis/public-apis) organizes free APIs: short rows, honest columns, links that work. **Not** a scrape of that list (or of build-your-own-x / awesome-selfhosted / awesome-go). Every blurb here is original.

PRs welcome: one link + 1–2 sentences you wrote. No star-farming.

## Index

- [Protocol & docs](#protocol--docs)
- [Facilitators](#facilitators)
- [Discovery](#discovery)
- [Live paid endpoints](#live-paid-endpoints)
- [Agent job boards](#agent-job-boards)
- [Skills & harnesses (related)](#skills--harnesses-related)
- [Tooling](#tooling)
- [Contributing](#contributing)

## Protocol & docs

| Link | Notes |
|------|--------|
| [x402.org](https://www.x402.org/) | Home of the open HTTP-native payment standard |
| [Seller quickstart](https://docs.x402.org/getting-started/quickstart-for-sellers) | Middleware → `402` → stablecoin settle |
| [x402 Foundation launch](https://x402.org/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications/) | Neutral home under the Linux Foundation |

## Facilitators

| Link | Auth | Notes |
|------|------|--------|
| [PayAI facilitator](https://facilitator.payai.network/) | None to hit | Common Base USDC facilitator; discovery crawls often follow it |
| [Coinbase CDP docs](https://docs.cdp.coinbase.com/) | Account for some flows | Official CDP / x402 tooling |

## Discovery

| Link | Notes |
|------|--------|
| [x402scan](https://www.x402scan.com/) | Indexes live `402` origins |
| [Agent402](https://agent402.tools/) | Agent tool router; often gates on settlement history |
| [PayAI](https://payai.network/) | Catalog / Bazaar; metadata can lag a live `402` |

## Live paid endpoints

Expect unpaid `GET` → **HTTP 402** with a payment challenge. Hosts on Cloudflare Workers Free can return **429** near the daily cap (often clears ~8 PM America/New_York).

| API | Price (approx) | Chain | Auth | HTTPS | CORS | Description |
|-----|----------------|-------|------|-------|------|-------------|
| [Spot FX `/fx`](https://api.premiumrewards.vip/fx?from=USD&to=EUR&amount=100) | $0.01 USDC | Base | x402 | Yes | * | ECB-spot-style FX check (Clear-to-Send) |
| [Pulse `/check`](https://pulse.premiumrewards.vip/check) | $0.005 USDC | Base | x402 | Yes | * | Tiny pre-spend probe before a larger buy |
| [Shop landing](https://premiumrewards.vip/) | free door | — | — | Yes | * | Human-readable entry; paid paths are the `402`s above |
| [Penniless Data Utilities `/repair/json`](https://penniless-json-repair.sjaman.workers.dev/repair/json) | $0.001 USDC | Base | x402 | Yes | * | 9 deterministic data/lookup tools (JSON repair, YAML→JSON, cron next-run, diff, extract, whois, DNS, repo-stats, email-validate); MCP at `/mcp` |

\* CORS: agent HTTP clients usually do not need browser CORS; treat as n/a for mute agent buyers.

Shop x402scan origin (canonical): `441bad1b-0ed0-4de6-a552-7f8234d2e501`

## Agent job boards

Wallet payout ≠ no KYC. Read each board.

| Board | Payout | Caveat |
|-------|--------|--------|
| [TaskMarket](https://taskmarket.daydreams.systems/) | On-chain | Escrow / legal bundle varies per task |
| [Superteam Earn](https://earn.superteam.fun/) | Mixed | Many listings need human KYC / human claim |

## Skills & harnesses (related)

These are **not** x402 products. They show what agents star right now (skills packs, harnesses, agency templates). Use them as format inspiration — do not clone their trees into a star farm.

| Repo | Why it trends |
|------|----------------|
| [obra/superpowers](https://github.com/obra/superpowers) | Agentic skills methodology |
| [mattpocock/skills](https://github.com/mattpocock/skills) | Practical engineer skills |
| [anthropics/skills](https://github.com/anthropics/skills) | Public Agent Skills |
| [msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents) | Multi-agent “agency” personas |
| [anomalyco/opencode](https://github.com/anomalyco/opencode) | Open coding agent |
| [firecrawl/firecrawl](https://github.com/firecrawl/firecrawl) | Context / scrape API (often paid SaaS) |

## Tooling

- Pair Cloudflare Workers (or Node/Hono) with x402 payment middleware; keep seller copy machine-shaped.
- Base USDC contract commonly used by sellers: `0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913`.

## Contributing

1. PR = one live URL + a short blurb you wrote.
2. Prefer endpoints that return real `402` (or clear docs).
3. No paid starring, no dumping other awesome lists, no fake badges.

## License

List text: [CC0 1.0](./LICENSE). Linked projects keep their own licenses.
