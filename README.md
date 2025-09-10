# Trader Behavior & Market Sentiment Analysis
1. Introduction
The goal of this analysis is to explore the relationship between trader performance (profitability, risk, volume, leverage) and market sentiment (Fear vs Greed). We aim to:
•	Identify patterns in trader behavior under different sentiment conditions.
•	Determine how profitability, risk, and trade volume vary across sentiments.
•	Detect clusters of trades and interpret their significance.
•	Provide actionable insights for smarter trading strategies.
 
2. Data Overview
Trades dataset columns:
['account', 'coin', 'execution_price', 'size_tokens', 'size_usd', 'side', 'timestamp_ist', 'start_position', 'direction', 'closed_pnl', 'transaction_hash', 'order_id', 'crossed', 'fee', 'trade_id', 'timestamp', 'time', 'date']
Fear/Greed dataset columns:
['timestamp', 'value', 'classification', 'date']
Data has been cleaned, normalized, and merged by date to align trades with market sentiment.
 
3. Metrics by Sentiment
Aggregated metrics include average PnL, standard deviation of PnL, total volume, average trade size, average leverage, and win rate for each sentiment category:
Sentiment	Avg PnL	Std PnL	Total Volume	Avg Volume	Avg Leverage	Win Rate
Extreme Fear	1.89	76.73	9.58M	4,119	21,903	0.29
Extreme Greed	205.82	1,861.56	18.22M	3,242	24,593	0.55
Fear	128.29	1,342.35	79.67M	5,745	8,146	0.38
Greed	53.99	1,399.47	57.05M	5,052	37,277	0.44
Neutral	27.09	142.95	11.94M	4,332	89,200	0.49
Observations:
•	Strong sentiment periods (Fear or Greed) have higher PnL and variability.
•	Win rate is lowest during Extreme Fear and highest during Extreme Greed.
•	Leverage is extremely high during Neutral periods, likely due to outliers.
 
4. Statistical Testing
T-test: Fear vs Greed PnL
t = 4.266, p ≈ 0.000
Interpretation:
•	The difference in PnL between Fear and Greed periods is statistically significant.
•	Traders earn higher PnL on average during Fear periods compared to Greed.
 
5. Clustering Trades
KMeans clustering (3 clusters) was applied using:
['size_usd','closed_pnl','fee']
Cluster Overview
Cluster	Avg Size	Avg PnL	Avg Fee	Avg Leverage	Count	Interpretation
0	~3,237	29	0.66	-30,480	208,369	Small trades, low PnL, retail/micro traders
1	~144,000	1,218	32	9,355	2,720	Medium-large trades, moderate-high PnL, professional traders
2	~926,000	6,836	150	1,994	135	Very large trades, high PnL, whales/institutional traders
 
Cluster Behavior Across Sentiments
Cluster	Sentiment	Avg PnL	Avg Size	Avg Leverage	Count
0	All	Low	Small	High	Many
1	Extreme Greed	Very High	Medium	Moderate	Few
2	Fear / Greed	High	Large	Low	Very Few
Insights:
•	Retail traders (Cluster 0) dominate small trades across all sentiments.
•	Medium-large traders (Cluster 1) profit most in Extreme Greed.
•	Whales (Cluster 2) make very large profitable trades, usually during Fear or Greed.
 
6. Visualizations
1.	Average PnL by Sentiment
2.	Total Trade Volume by Sentiment
3.	Win Rate by Sentiment
4.	Clusters of Trades (scatterplot with sentiment overlay)
(All visualizations use vibrant, distinguishable colors and clear axes for easy interpretation.)
 
7. Key Insights for Trading Strategy
1.	Profitability aligns with strong sentiment: Fear → high-risk/high-reward trades, Greed → moderate-risk profitable trades.
2.	Risk management is critical: retail traders with high leverage risk losses in extreme sentiment periods.
3.	Clusters reveal trader archetypes: retail, professional, whales – each responds differently to market sentiment.
4.	Actionable strategy:
o	Exploit Fear periods carefully with calculated risk.
o	Use Greed periods for moderate, safer trades.
o	Whale/large-trade signals can inform liquidity opportunities.
![Uploading image.png…]()
