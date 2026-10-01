# Fundamental Value Entry

A price-blind, versioned equity valuation and monitoring system — packaged as a portable Skill.

## What it does

1. **Valuation kernel** — builds intrinsic value (Bear / Base / Bull → probability-weighted) *before* looking at the current price, then locks fixed entry zones: **RB** (Reasonable Buy), **HV** (High Value), **EV** (Extreme Value).
2. **Tiered monitoring** — FOCUS / CORE (`daily_core: true`) get daily lightweight scans; EXTENDED (`daily_core: false`) is event-driven radar. Tiers change monitoring frequency only, never intrinsic value.
3. **Event escalation** — material catalysts and abnormal moves (default **8%** single-session, **5%** for FOCUS) queue deep review; one idempotent heavy-review job runs after each U.S. close (16:10 ET).
4. **Sleeve separation** — valuation, momentum, market state, and execution stay in separate layers. A price move triggers investigation, never automatic revaluation.

## What's inside

```
skill/fundamental-value-entry/
├── SKILL.md                        # runtime contract and invariants
├── references/
│   ├── valuation-models.md         # TRADITIONAL and HIGH_CONVEXITY construction
│   ├── monitoring-policy.md        # FOCUS / CORE / EXTENDED behavior
│   ├── review-triggers.md          # 8%/5% rules and post-close idempotency
│   ├── registry-schema.md          # versioned valuation + runtime-state schema
│   ├── source-policy.md            # source hierarchy and freshness
│   ├── momentum-entry-framework.md  # optional execution overlay
│   ├── valuation-record-template.md # per-ticker record format
│   ├── worked-example-nvda.md      # full NVDA walkthrough (illustrative)
│   └── lessen_learnrd.md           # incident-derived permanent controls
├── agents/openai.yaml
└── assets/icon.svg
config/
├── universe.yaml                   # tier definitions (ships with empty watchlist)
├── monitoring.yaml                 # scan + heavy-review policy
├── defaults.yaml
└── execution-policy.yaml           # valuation/momentum/holdings separation
```

## Capacity

This edition tracks up to **10** securities with ACTIVE valuations. State is kept in local files (one valuation record per ticker plus a registry index) — no accounts, no API keys, no external database.

## Quickstart

Install the Skill in your agent, then:

- `"Value NVDA and set it up for monitoring"` — full chain: identity → tier → price-blind scenarios → locked zones → monitoring.
- `"Run today's post-close heavy review"` — reconciles filings, events, and pending deep reviews for the trading date.
- `"What fired today?"` — lightweight scan output: EV names first, then HV, then triggers.

See `skill/fundamental-value-entry/references/worked-example-nvda.md` for a complete annotated run.

## Disclaimer

This Skill is an analytical framework for investment research. It is not financial advice, investment advice, or a recommendation to buy, sell, or hold any security. It does not execute trades. Only the user decides what to buy or sell, and only with capital they can afford to lose.
