# Spirit Tea — Founder Dashboard

Live wholesale (B2B) reporting for Spirit Tea, built for Jordan.

**Live URL:** https://marketingheroe-arch.github.io/spirit-tea-founder-dashboard/

## What it shows

| Tab | Contents |
|---|---|
| Overview | Wholesale revenue, incoming leads, lead-to-close, Enterprise share, revenue by month, risk buckets |
| Team | Revenue per rep, full rep table, outbound leads generated, leads closed |
| Accounts | Enterprise accounts, slipping accounts (90–365d), at-risk / churned (>365d) |
| Products & Matcha | Matcha share of revenue, private label vs catalogue, product tier mix, matcha revenue by SKU |
| How to read this | Definition of every metric, plus what the dashboard cannot see |

## Data

- Source: HubSpot portal 22533061 — Orders (0-123), Companies, Deals, Line items.
- Read live through the Cloudflare Worker proxy `super-limit-2f74.marketing-heroe.workers.dev`.
- Orders are searched in **one-month windows** to stay under HubSpot's 10,000-record paging ceiling.
- Product revenue spreads each order's discount across its line items pro-rata, so product figures
  reconcile to the revenue total. (Measured August 2026: discounts were 9.0% of revenue.)
- Verified 2026-09-07 against the independent CMO orders worker — August 2026 matched to the cent:
  866 orders, $870,775.05, AOV $1,005.51.

## Scope and caveats

- **Wholesale only.** The B2C retail store is a separate Shopify and does not sync into HubSpot.
- Enterprise share is a **floor** — only a small share of accounts carry a Segment tag today.
- Never reconcile against GA4: GA4 sees roughly half of wholesale revenue because private-label
  orders are created as drafts and skip web checkout.

## Maintenance

Everything is one self-contained file (`index.html`) with no external dependencies.
Edit it, commit, and GitHub Pages redeploys automatically. **Hard-refresh (Ctrl+Shift+R)** after a
deploy or you will see the cached version.

Rep roster lives in `const OWNERS`; adding a rep there is enough — every table and chart derives from it.

Light theme only, by design.
