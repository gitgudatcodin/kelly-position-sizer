# Kelly Position Sizer

Size stock positions with the Kelly criterion (`f* = p − (1−p) / b`).

## Run

```bash
pip install -r requirements.txt
streamlit run app.py
```

## What it does

1. **Edit the stock table** — ticker, win probability, current price, 12-month
   target, downside if your thesis is wrong, and beta. Add or delete rows freely.
   Pre-loaded with 14 research names (Sept 26, 2026 data).
2. **Tune assumptions** (sidebar) — Kelly fraction (default half-Kelly),
   win-probability sensitivity shift, cash reserve, max position cap, dust
   threshold, and the covariance model's market/idiosyncratic volatilities.
3. **Get the portfolio** — an edge table (who earns a bet), the long-only
   growth-optimal portfolio (`w = Σ⁻¹μ`), fractional-Kelly sizing with your
   caps, dollar amounts for your portfolio value, and expected return/vol.

## The math

- Per bet: `f* = p − (1−p)/b`, with `b = upside/downside`
- Expected return: `μ = p·upside − (1−p)·downside`
- Portfolio: long-only growth-optimal `w = Σ⁻¹μ`, covariance from a
  single-index model `Σ = σₘ²ββᵀ + σₑ²I`, then your Kelly fraction, caps,
  dust filter, and cash reserve.

Research analysis tooling, not investment advice.
