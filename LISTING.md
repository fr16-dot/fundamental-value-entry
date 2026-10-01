# Capafy Listing Draft — Fundamental Value Entry

> Working draft. Fill in screenshots and final pricing before submitting.

## Title

Fundamental Value Entry

## Tagline

Price-blind intrinsic valuation plus tiered daily monitoring for up to 10 stocks.

## Short description (for cards)

Value stocks like an analyst, not a chart-reader: lock Bear/Base/Bull intrinsic value *before* seeing the price, get fixed RB/HV/EV entry zones, and let the agent watch your 10-stock universe daily — escalating only real catalysts and abnormal moves into deep review.

## Long description

Most investors anchor on price first and justify later. Fundamental Value Entry reverses the order:

1. **Price-blind valuation.** The agent gathers filings and fundamentals, assigns a model class (TRADITIONAL or HIGH_CONVEXITY), builds Bear/Base/Bull scenarios, and locks a probability-weighted fair value — all before retrieving the current quote.
2. **Fixed entry zones.** Fair value converts into three zones that never move with price: Reasonable Buy (10–20% discount), High Value (20–35%), Extreme Value (>35%). Zones change only on material fundamental evidence.
3. **Tiered monitoring.** FOCUS and CORE names get daily lightweight scans; EXTENDED is low-cost radar. A single-session move of 8% (5% for FOCUS) or any material catalyst queues deep review — never an automatic revaluation.
4. **One post-close review per day.** A single idempotent heavy-review job runs after each U.S. close, reconciling filings, events, and pending reviews for that trading date.
5. **Separate sleeves.** Valuation, momentum timing, market state, and execution stay in separate layers with separate invalidation rules.

No accounts, no API keys, no external database: state lives in local files, one record per ticker. Includes a fully worked NVDA example so you can see the output before you subscribe.

**Capacity:** up to 10 actively tracked securities.
**Not financial advice.** This is an analytical framework for investment research; it does not execute trades and does not tell you what to buy or sell.

## Tags

investing, stocks, valuation, value-investing, watchlist, DCF, stock-analysis, portfolio

## Pricing (suggested)

- **$19.99/month**, free trial, Run Online.
- Rationale: full value+momentum dual system with tiered monitoring and idempotent daily review; priced between casual screeners and professional terminals.

## Screenshots to prepare

1. Tier table (FOCUS / CORE / EXTENDED) from `references/monitoring-policy.md`.
2. NVDA worked-example excerpt: locked zones + price mapping.
3. Sample daily scan output (EV first, then HV, then triggers).
4. Deep-review escalation: 8% trigger → pending → post-close reconciliation.

## Pre-flight checklist

- [ ] Capafy creator account created (no publish/KYC until approved).
- [ ] `capafy publish init` run against a local clone of this repo.
- [ ] **Run Online persistence test:** create two valuation records in one session; open a new session the next day and confirm the files persist. If not, switch listing to Download or add buyer-supplied storage.
- [ ] Live quote + filings access verified in the Run Online sandbox.
- [ ] Screenshots uploaded; pricing and trial set.
- [ ] Investment disclaimer present in listing copy (above) and in SKILL.md.
