# Wine-Searcher MCP — LWIN Pricing & Scores for Wine Trade

[![Listed on mcpmarket.com](https://img.shields.io/badge/Listed_on-mcpmarket.com-blue)](https://mcpmarket.com/server/wine-searcher-mcp)
[![Apify Actor](https://img.shields.io/badge/Apify-Actor-orange)](https://apify.com/mrbridge/wine-searcher-scraper-from-list?fpr=mrbridge)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Public configuration + documentation for the **Wine-Searcher MCP**, a Model Context Protocol bridge to the [`mrbridge/wine-searcher-scraper-from-list`](https://apify.com/mrbridge/wine-searcher-scraper-from-list?fpr=mrbridge) Apify Actor.

Look up wine pricing, critic scores, and popularity rankings from Wine-Searcher directly inside Claude, Cursor, Cline, or any MCP client. Pay only for successfully extracted wines ($0.025/wine, success-only billing).

## What's in this repo

- **MCP client configuration** snippets for Claude Desktop, Cursor, and Cline (see [`examples/`](examples/))
- **README** mirroring the [mcpmarket.com listing](https://mcpmarket.com/server/wine-searcher-mcp)
- **Logo and visual assets** ([`assets/`](assets/))
- **Issues**: bug reports and feature requests welcome

The actual scraping logic, anti-detection stack, and proxy management live in the Apify Actor (not in this repo). This repo is **client configuration only**.

## Quick start

1. [Get a free Apify token](https://apify.com/?fpr=mrbridge) ($5 in starter credits = ~200 wines)
2. Copy the config snippet for your client (e.g. [Claude Desktop](examples/claude-desktop.json))
3. Set `APIFY_TOKEN` in your environment
4. Restart your MCP client — Wine-Searcher tools are now available to your AI agent

## Example queries to ask your AI

After installation:

- *"Look up Wine-Searcher prices for these LWIN codes: 11316442021, 11084042019."*
- *"What's the cheapest 2015 Château Margaux worldwide right now?"*
- *"Compare critic scores and per-bottle prices for Petrus 2015 vs Cheval Blanc 2015."*

## Pricing

**$0.025 per wine extracted. No subscription.**

- ✅ Wine successfully extracted → $0.025
- ❌ Wine not found / blocked / timeout / invalid input → free

Full pricing details and free trial credits on the [Apify Actor page](https://apify.com/mrbridge/wine-searcher-scraper-from-list?fpr=mrbridge).

## What the scraper extracts

13 structured fields per wine, including:

- Wine name, appellation, vintage
- Critic score (0-100), reviews count
- Cheapest worldwide price (per 75cl bottle, currency-normalized)
- Cheapest merchant
- Winery name, winery URL
- Wine-Searcher popularity ranking
- Wine-Searcher direct URL
- Bottles per unit (1 = single bottle, ≥2 = case auto-normalized)
- Scraped-at timestamp

Full output schema documented on the [Apify Actor page](https://apify.com/mrbridge/wine-searcher-scraper-from-list?fpr=mrbridge).

## Limitations

- Max 1000 wines per single MCP call (large lists → batch)
- Public listings only — no authenticated Wine-Searcher account features
- Per-bottle normalization assumes "Case of N" patterns; non-standard case formats may fall through
- Excludes auctions, pre-arrival, and "by request" offers from the cheapest-price calculation

## Support

- **Bug reports**: open a [GitHub Issue](https://github.com/MrBridgeHQ/wine-searcher-scraper-mcp/issues)
- **Feature requests**: same, with the `enhancement` label
- **Commercial integrations**: contact via the [Apify Actor support form](https://apify.com/mrbridge/wine-searcher-scraper-from-list?fpr=mrbridge)

## Related projects

This MCP is part of a wine-data toolkit:

- [Wine-Searcher Grape Scraper](https://apify.com/mrbridge/wine-searcher-grape-scraper?fpr=mrbridge) — discover wines by grape variety
- [Vivino Wine Data Scraper](https://apify.com/mrbridge/vivino-wine-data-scraper?fpr=mrbridge) — Vivino ratings + taste profiles
- [Millesima Wine Scraper](https://apify.com/mrbridge/millesima-wine-scraper?fpr=mrbridge) — Millesima.fr prices and critic ratings

All powered by [Apify](https://apify.com/mrbridge?fpr=mrbridge).

## License

MIT — see [LICENSE](LICENSE).

The MIT license covers this configuration repo only. The underlying Apify Actor is proprietary; usage governed by [Apify's Terms of Service](https://apify.com/terms?fpr=mrbridge).
