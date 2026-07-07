# Trader Performance vs Market Sentiment — Summary Write-up

## Methodology

Two datasets were combined: Hyperliquid trade-level data (~211K trades, 32 accounts) and the
daily Bitcoin Fear & Greed Index (2018–2025). Trade timestamps were converted to dates and
merged with the sentiment classification active on that date (99.99% match rate). Per-trader,
per-sentiment metrics were computed (total PnL, average PnL per trade, win rate, trade
frequency, average trade size, long/short bias, and a max-drawdown proxy). Traders were
further split into two behavioral segments: **Frequent vs Infrequent** (by total trade count)
and **Consistent vs Inconsistent** (by variability of win rate across sentiment regimes).

## Key Insights

1. **Extreme Greed shows the strongest performance.** Average PnL per trade is highest during
   Extreme Greed ($67.89) and win rate peaks at 46.49%, compared to Extreme Fear ($34.54 avg
   PnL, 37.06% win rate) — the weakest regime overall.

2. **Sentiment score alone is a weak linear predictor.** Correlation between the continuous
   Fear & Greed score and daily aggregate PnL is only -0.083 — near zero. This means the
   relationship is not simply "higher score = higher profit"; performance is better explained
   by the *categorical* regime (see #1) than a linear score, suggesting a non-linear,
   extremes-driven effect rather than a steady trend.

3. **Trader behavior shifts noticeably with sentiment.** Long positioning bias is highest
   during Fear regimes (~57–62% long) and lowest during Greed (~33–34% long) — a somewhat
   contrarian pattern, not what a naive "greed = more longs" assumption would predict. Trade
   frequency is also far higher during Extreme Fear (~1,529 trades/day) than during Greed
   regimes, suggesting fear periods drive more active (possibly reactive) trading.

4. **Consistency matters more than activity level.** Traders classified as "Consistent"
   (stable win rate across all five sentiment regimes) had both a higher average win rate
   (41.5% vs 39.1%) and higher average total PnL ($344K vs $297K) than "Inconsistent" traders,
   whose performance swings heavily with market mood. This suggests durable trading edge is
   more sentiment-independent than regime-dependent.

## Strategy Recommendations

1. **Reduce position sizing during Extreme Fear.** With the lowest win rate (37.06%) and
   highest trade frequency of any regime, Extreme Fear periods combine weaker edge with
   more active (likely emotionally-driven) trading — a risk-increasing combination. Traders
   should scale down size or tighten risk limits specifically in this regime.

2. **Favor consistency over sentiment-chasing.** Since Consistent traders outperform
   Inconsistent traders on both win rate and total PnL, strategies should prioritize stable,
   repeatable rules over adjusting aggressively to each sentiment swing. Inconsistent traders
   in particular should consider reducing size during regimes where their historical win rate
   (per the Section 14 heatmap/table) is weakest, rather than trading their normal size
   regardless of regime.

## Bonus: Predictive Model

A Random Forest classifier was trained to predict next-day profitability bucket (Low /
Medium / High) using same-day sentiment score and trading behavior as features. It achieved
~49% test accuracy against a 33% random baseline (3 balanced classes) — a moderate but real
signal. Feature importance showed a trader's own recent behavior (daily PnL, average trade
size, trade count) mattered more than the sentiment score itself, reinforcing insight #4:
individual trading pattern is a stronger driver of near-term outcomes than market mood alone.
