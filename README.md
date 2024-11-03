# Application Programming for Financial Engineering

### Project 1: Optimizing Trading Schedules with Dynamic Programming

This project focused on using dynamic programming to determine the optimal trading schedule over multiple time periods. The primary goal was to maximize the number of successfully traded shares by considering both the number of shares to sell at each time step and the impact of previously traded shares. 

Key highlights of the project included:

Dynamic Programming Approach: A vectorized approach was implemented, with a focus on leveraging cached trade success rates to streamline computations.

Backtracking for Optimal Sequence: A trace table was used to reconstruct the optimal trading schedule by backtracking through previous results.

Scoring System: The effectiveness of the trading schedule was evaluated on historical data, utilizing a scoring mechanism that restricted trades to realistic volumes.

Parameter Optimization: Determined an optimal parameter, π, to maximize trading effectiveness. Iterative testing identified an approximate value, balancing conservativeness and aggression in trading. 

The project also includes throughly analyzing of each parameters and their features, how they correlated with the scores.


### Project 2: Portfolio Optimization and Risk Management

This project delved into portfolio optimization, with a key objective to maximize returns while considering risk management. 

Unlike traditional optimization, this project introduced a unique approach:

Highest Revenue with Risk Constraints: While the objective was to maximize portfolio revenue, the analysis revealed that selecting the highest revenue portfolio involved concentrating on a single stock, which posed significant risk. Instead, a diversified portfolio that invested in at least four stocks was selected. This portfolio demonstrated a high and stable revenue, reflecting a more balanced risk-reward profile.

Dynamic Adjustments: Various investment strategies were explored, and the final selection emphasized both high returns and reduced risk exposure.

Strategic Diversification: The project underscored the importance of not merely focusing on maximum returns but also incorporating risk-adjusted considerations for a sustainable investment approach.

Still, the project also includes a deep understanding of all parameters appeared, how they influence the objective, which trend is expected if they increase or decrease.


### Project 3: Anomaly Detection in Financial Data using Eigenvalue Analysis

This project addressed the detection of data anomalies (referred to as “pollution”) in financial datasets, using advanced eigenvalue and interval testing techniques. 

This project consisted of:

Power Method for Eigenvalue Calculation: The project utilized the power method to compute the dominant eigenvalue, a key indicator for identifying intervals with unusual covariance structures.

Interval Testing and Heatmaps: By analyzing both original and differenced data, intervals with significantly elevated eigenvalues were identified as candidate polluted intervals. Heatmaps and other visualizations highlighted regions with high covariance, reinforcing the hypothesis of correlated anomalies.

Validation through Random Walk Analysis: Additional plots demonstrated how the identified polluted intervals exhibited patterns inconsistent with typical random walk behavior, suggesting these intervals were genuinely anomalous rather than random fluctuations.

Comprehensive Interval Selection: The project meticulously analyzed multiple intervals, ultimately selecting an interval where anomalies consistently manifested across different analyses.
