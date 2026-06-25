# 3Jane Farm Calculator

A static GitHub Pages calculator for estimating 3Jane farm returns.

## Data Sources

- 3Jane Convex: `https://opulent-crocodile-74.convex.cloud`
- 3Jane Farm: `https://app.3jane.xyz/farm`
- Pendle API: `https://api-v2.pendle.finance`
- Morpho API: `https://api.morpho.org/graphql`
- Curve API: `https://api.curve.finance/api`

## Calculation Notes

- Default holding period is the number of days from today to `2026-12-17`, the Pendle YT expiry date.
- Default assumptions are `100M` JANE FDV and `3.33B` JANE supply.
- JANE price is calculated as `JANE FDV / JANE supply`.
- JANE APR is recomputed from live 3Jane emissions using the user-provided JANE price.
- 3Jane live emissions APR is first normalized from the app's original `250M FDV / 6.66B supply` baseline.
- YT strategies use the live Pendle YT price to calculate purchasable YT amount.
- YT JANE rewards are calculated on purchased YT notional, then converted back to APR on user principal.
- YT base return is net of expiry loss: `YT notional yield - YT purchase cost that goes to zero at expiry`.
- YT TVL is shown as reward denominator notional multiplied by the live YT price when available.
- Pendle PT TVL falls back to live Pendle market liquidity plus orderbook size when the 3Jane emissions TVL is zero.

## GitHub Pages

1. Push `index.html`, `styles.css`, `app.js`, `README.md`, and `.nojekyll` to the repository root.
2. Open GitHub repository `Settings` -> `Pages`.
3. Select `Deploy from a branch`.
4. Select branch `main` and folder `/root`.

No build step is required.
