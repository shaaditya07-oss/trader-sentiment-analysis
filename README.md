# trader-sentiment-analysis
Trader Performance vs Market Sentiment Analysis

Analysis of how Bitcoin market sentiment (Fear & Greed Index) relates to trader behavior and
performance on Hyperliquid, using historical trade-level data.

Objective

Uncover patterns between market sentiment (Extreme Fear → Extreme Greed) and trader
profitability, behavior, and risk — to inform sentiment-aware trading strategy rules.

Datasets

FileDescriptionhistorical_data.csvTrade-level data from Hyperliquid (account, coin, execution price, size, side, PnL, timestamp)fear_greed_index.csvDaily Bitcoin market sentiment score and classification (2018–2025)

Repository Structure

├── trader_sentiment_analysis.ipynb      # Main analysis notebook (fully executed)
├── historical_data.csv                  # Raw trade data
├── fear_greed_index.csv                 # Raw sentiment data
├── writeup.md                           # 1-page summary: methodology, insights, strategy
├── trader_performance_by_sentiment.csv  # Output: per-trader performance by sentiment
├── overall_performance_by_sentiment.csv # Output: market-wide performance by sentiment
├── trader_segments.csv                  # Output: trader segment assignments
└── *.png                                # Output charts

How to Run


Clone this repository:


   git clone <repo-url>
   cd <repo-folder>


Install dependencies:


   pip install pandas numpy matplotlib seaborn scikit-learn jupyter


Launch Jupyter and run all cells top to bottom:


   jupyter notebook trader_sentiment_analysis.ipynb

All outputs (tables, charts, model results) will regenerate in order — the notebook is
fully reproducible from the two raw CSV files.

Analysis Overview


Data preparation — cleaning, date alignment, merge of trade and sentiment data
Performance analysis — PnL, win rate, and ranking of traders across 5 sentiment regimes
Behavioral analysis — trade frequency, position size, and long/short bias by sentiment
Risk analysis — drawdown proxy by sentiment regime
Segmentation — Frequent vs Infrequent traders, Consistent vs Inconsistent winners
Bonus: Predictive modeling — Random Forest classifier predicting next-day
profitability bucket (Low/Medium/High) from sentiment + behavior features


See writeup.md for the summarized methodology, key insights, and strategy recommendations.

Author

Aditya Kumar Sharma
