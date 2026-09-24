### Econometrics and machine learning on market data

Final-year BSc Economics student at the University of Birmingham. I work on
empirical questions about markets where the answer depends on getting the
inference right: standard errors that match how the data were generated,
out-of-sample tests against a linear baseline, and keeping descriptive, causal
and predictive claims apart.

Not everything I expected held up. In the Bitcoin study my main hypothesis
failed, and in the earnings study two of the three moderators an earlier
version reported as significant disappeared once the standard errors were
fixed. Both READMEs say so.

---

#### Research

**[Cross-exchange price discovery in Bitcoin](https://github.com/ChistoOleg/price-discovery)**  
*When news hits bitcoin, which venue's price moves first: Binance, Coinbase or Kraken?*  
Eleven days of top-of-book quotes collected live over websockets (about 114
million ticks, reduced to a one-second grid), a cointegrated VECM with a
hand-written Johansen estimator, Hasbrouck information shares, Gonzalo-Granger
component shares, block-subsample confidence intervals and a sup-Wald break scan.  
Result: Coinbase, not the much larger Binance, takes the largest component
share (0.66, 90% CI 0.62 to 0.70). The ranking holds across USDT-conversion
treatments, lag lengths, subsamples, trading sessions and volatility regimes.
Information-share bounds are too wide to rank the venues at one-second
resolution, so the claim stays narrow.

**[Earnings Reaction Lab](https://github.com/ChistoOleg/earnings-reaction-lab)**  
*Why do similar earnings surprises produce such different price reactions?*  
48,056 announcements from 730 S&P 500 constituents, 2006 to 2026, on
point-in-time index membership. Post-double-selection lasso, a causal forest
with a best linear projection on cross-fitted residuals, and LightGBM against
OLS and Ridge under purged walk-forward cross-validation.  
Results: a one-standard-deviation surprise moves the two-day abnormal return by
0.7 to 0.8 pp, and three estimators agree on that. The effect shrinks by up to
a factor of four during the financial crisis and COVID. Firm size is the only
moderator that survives firm-clustered errors (the naive errors were up to 33
times too small). LightGBM beats OLS on squared error (Diebold-Mariano
p < 0.001), but its rank-IC edge, 0.241 against 0.235, has a bootstrap interval
that includes zero.
[`FIXES-2026-09.md`](https://github.com/ChistoOleg/earnings-reaction-lab/blob/main/docs/FIXES-2026-09.md)
logs the 30 defects found and fixed along the way.

---

#### Tools and systems

**[Regulatory exposure scoring](https://github.com/ChistoOleg/regulatory-exposure-scoring)**  
Ranks European companies by their exposure to carbon regulation. It started as
a sales-targeting problem during an internship at a climate-software company.
The main signal comes from EEA EU ETS registry data (84,056 rows): the share of
a sector's verified emissions not covered by free allocation, by country. It
comes out at 0.87 for German power and 0.00 for German metals, which is what
the allocation rules would predict. Every score returns its own arithmetic and
the maximum reachable from data that can actually be obtained. Standard library
only, 92 tests.

**[Market Intelligence Bot](https://github.com/ChistoOleg/market-intel-bot)**  
Self-hosted Telegram bot that sends scheduled cross-asset digests, per-ticker
news alerts with an LLM read on sentiment and impact, and price alerts.
Owner-locked, SQLite storage, Docker, 36 tests in CI.

---

#### Methods and tools

Cointegration and VECMs · information and component shares · double-selection
lasso · causal forests · clustered and HAC inference · block bootstrap · purged
walk-forward CV · structural-break tests

`Python` · `pandas` · `NumPy` · `SciPy` · `statsmodels` · `scikit-learn` ·
`LightGBM` · `EconML` · `DoubleML` · `SHAP` · `Optuna` · `asyncio` ·
`websockets` · `SQLite` · `Docker` · `GitHub Actions`

