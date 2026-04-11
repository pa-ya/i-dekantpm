# DekantPM Improved - Mathematical Analysis and Economic Refinements

An interactive, offline-first document and playground for continuous prediction markets using an L2-norm AMM, with a stronger focus on economics: profitability analysis, payout fairness, price clarity, and trade impact visibility.

## Origin

This repository is an improved continuation of the original project:

- Original repo: https://github.com/pa-ya/dekantpm
- Original live demo: https://pa-ya.github.io/dekantpm

## What This Project Is

`DekantPM Improved` combines:

- A mathematical document (with formulas, proofs, and design rationale)
- An interactive market playground (discrete and distribution trading)
- LP tools for fee and break-even intuition
- Offline-first HTML/CSS/JS (no build step required)

## Why This Improved Version Exists

This version is focused on practical market economics, especially:

- Better probability interpretation for traders
- Better payout behavior around bin boundaries
- Better profitability diagnostics for traders and LPs
- Better visibility into trade impact (useful for slippage-aware decisions)

## Key Improvements vs Original `dekantpm`

1. Linear probability display (no quadratic distortion)
- Uses `p_i = x_i / sum_j x_j` in the UI and analytics.
- Removes the old quadratic display distortion where shown probability could diverge from true marginal pricing.

2. Smooth settlement kernel (`W`, default `3`)
- Resolution now supports kernel-weighted payouts across nearby bins instead of strict winner-take-all bin cliffs.
- Near-miss predictions can receive partial payout, improving continuity and reducing hard boundary effects.

3. Kernel-aware portfolio and P&L math
- Expected payout, peak payout, and unrealized P&L are computed using kernel-aware outcomes.
- Portfolio metrics better reflect actual resolution mechanics.

4. LP economics cleanup and clearer break-even behavior
- LP calculator logic is updated to reflect the improved baseline assumptions.
- Fee, LP share, redemption fee, and kernel width are explicit and configurable.

5. Better trade preview tooling (buy/sell)
- Preview cards show fee, tokens/received amount, peak payout, max profit, and post-trade probability.
- Preview charts help estimate trade impact before execution (useful as a slippage proxy).

6. State and configuration updates
- Improved state key/versioning for local persistence.
- Kernel width is part of per-market configuration and persisted state.

## Features

- Multi-market simulation with global traders
- Discrete and Gaussian-weighted distribution trading
- Per-market fee controls (trade fee, LP fee share, redemption fee, kernel width)
- Market overview, trade history, and action log
- Portfolio analytics (wallet, invested/received, expected payout, peak payout, net P&L)
- LP add/remove flows and break-even calculator
- Resolve and re-resolve flows for scenario testing
- Theme/language/settings controls and autosave

## Project Structure

```text
i-dekantpm/
|- index.html           # Main document and UI
|- math_doc_script.js   # Market engine + interactions + persistence
|- fonts/
|  |- fonts.css
|  `- *.ttf
`- lib/
   |- chart.umd.min.js
   `- tex-svg.js
```

## Getting Started

Open `index.html` in a modern browser.

No package install, build step, or backend is required.

## Notes

- This is a research/educational simulator and math playground, not financial advice.
- If you are familiar with the original `dekantpm`, start with the Probability Distortion section and Resolution section to see the main economic model changes quickly.
