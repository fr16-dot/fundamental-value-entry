# Worked Example — NVDA (illustrative)

> Illustrative example only. Figures use data available at the 2026-09-30 U.S. close. This is not a recommendation to buy, sell, or hold NVDA.

## 1. Identity and tier

- Security: NVIDIA Corporation, NASDAQ: NVDA, USD, common shares.
- Identity gate: passed (issuer, exchange, currency, share class verified; no corporate-action discontinuity).
- Tier: **CORE** (`daily_core: true`, standard daily monitoring, abnormal-move threshold **8%**).
- Model class: **TRADITIONAL** — operating economics and normalized cash generation are observable; conventional forecasting applies.

## 2. Price-blind fundamentals (before looking at price)

- FY2026 revenue $215.9B (+114% y/y); net income $120.1B (+145%); EPS $4.90.
- Gross margin 75%; net margin 55.7%; R&D $16.9B (+48% — reinvestment, not bloat).
- TTM revenue $303.0B; operating cash flow $181.2B (cash conversion is real, not accounting).
- Q2 FY27: revenue $96.2B (+106%), data-center $76.5B (+170%), EPS $1.08; Q3 guide ~$108B.
- Balance sheet: debt/equity 0.14, current ratio 3.86, $150B buyback authorization.
- Quality grade: **A** — dominant compute franchise, but cyclical end-market exposure caps the grade at the top end.

## 3. Locked scenarios (price still unseen)

| Scenario | Key assumptions | Value/share |
|---|---|---:|
| Bear | AI capex cycle corrects; data-center growth stalls to +5%; margin compression to 60% gross | $165 |
| Base | Data-center revenue CAGR ~18% for 10 years; terminal EBIT margin 45%; WACC 10% | $245 |
| Bull | Sovereign-AI demand sustains +25% CAGR; networking/software attach adds margin | $310 |

Probability weights: Bear 30 / Base 50 / Bull 20.
**Probability-weighted fair value: $234.**

Fixed entry zones (10–20% / 20–35% / >35% discount to fair):

- **RB (Reasonable Buy): $187–210**
- **HV (High Value): $152–187**
- **EV (Extreme Value): below $152**

Version saved as ACTIVE v1. Zones are now locked.

## 4. Price mapping (only now)

- 2026-09-30 close: **$228.38** (+1.5% session), quote fresh and valid.
- $228.38 vs. fair $234 → ~2.5% below fair → **fairly valued, no zone, no action.**
- Conclusion stated explicitly: fairly valued is a valid output. No zone is invented.

## 5. Trigger drill (what happens on a shock)

Suppose the next session NVDA falls **8.5%** on sector-wide news:

1. `abs(single_session_return) = 8.5% >= 8%` → `deep_review_pending: true`, reason `PRICE_ANOMALY`. Valuation version untouched.
2. Scheduled heavy review (16:10 ET, idempotency key `heavy_review_trading_date`) picks it up.
3. Investigation finds: no NVDA-specific fundamental change; move is sector beta. **Version stays ACTIVE v1**; review metadata refreshed; pending flag cleared with reason recorded.
4. If that trading date's heavy review already shows COMPLETED, a second run is refused — the pending item waits for the next scheduled job or an explicit manual deep dive.

## 6. Momentum overlay (separate sleeve)

With price above RB and a strong uptrend, the momentum module may track continuation — but it **may not** change the value sleeve's no-action conclusion, and it may not rewrite the $234 fair value. Entry on momentum requires its own pullback/confirmation plan per `references/momentum-entry-framework.md`.

---

**What this example demonstrates:** identity gate → tier assignment → price-blind scenarios → locked zones → price mapping → trigger escalation → idempotent review → sleeve separation. One prompt ("value NVDA and set up monitoring") runs the whole chain.
