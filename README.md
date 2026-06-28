# Electricity Price Forecasting — German Energy Market

Day-ahead electricity prices in Germany are highly volatile. They shift every hour based on how much electricity is being generated, consumed, and traded across borders. For energy traders, industrial companies, and grid operators, accurately anticipating these shifts is the difference between smart decisions and costly ones.

This project uses historical electricity market data from **SMARD** — Germany's official market transparency platform — to forecast day-ahead prices and understand what drives them.



## The Problem

Electricity cannot be stored at scale, so supply and demand must balance every single hour. When they don't, prices react sharply. Poor price forecasts lead to:

- Overpaying for electricity procurement
- Missed trading opportunities
- Unnecessary balancing costs
- Financial exposure during price spikes



## What I've done

A simple forecasting system that predicts Germany's hourly day-ahead electricity prices — and more importantly, explains *why* prices move the way they do.

The project is split into two parts:

**Exploratory Analysis** — Before modeling, 
- I investigated the market itself:
   - how prices fluctuate across hours, days, and seasons;
   - how renewable vs. conventional generation affects pricing;
   - how cross-border electricity flows between Germany and neighboring countries (France, Netherlands, Austria, Poland, and others) ripple into domestic prices;
   - how balancing reserve costs signal periods of market stress.




**Machine Learning Forecasting** — I trained and compared multiple gradient boosting models (XGBoost, LightGBM, CatBoost) on a chronological train-test split to avoid data leakage. Beyond standard error metrics, 
 - I evaluated the models on what matters operationally:
   - directional accuracy (does the model correctly predict whether prices go up or down?),
   - volatility capture (does it track price swings?),
   - extreme price movement detection (does it flag spikes above 15% change?).

I also added 95% confidence intervals to every prediction, so users get a price range rather than a false point estimate.



## Key Takeaways

- Renewable generation pushes prices down — more solar and wind supply shifts the merit order and suppresses market prices.
- Demand drives prices up — peak consumption hours and weekdays consistently produce higher prices.
- Neighboring countries matter — Germany's interconnected position in Europe means French, Dutch, and Austrian prices directly influence what happens domestically.
- Balancing costs are a stress signal — high reserve activation and TSO costs reliably coincide with price volatility.
- Time patterns are strong predictors — hour of day, weekday, and season are among the most informative features, because electricity demand follows human behavior.



## Future Directions

- Integrating weather forecast data (temperature, cloud cover, wind speed) as leading indicators
- Extending the system to forecast electricity demand alongside prices
- Probabilistic forecasting with tighter confidence intervals
- Real-time prediction dashboard



*Data source: [SMARD — Bundesnetzagentur](https://www.smard.de)*  
*[PowerCast: The Electricity Price Forecasting Challenge](https://app.lunor.ai/quest/1000033)*
