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


### Project 4: Portfolio Construction with Gradient-Based Optimization

This project centered on constructing an optimized long-only portfolio using daily stock price data, with an emphasis on solving custom risk-return tradeoff problems through gradient-based methods.

The project introduced two primary tasks:

Task 1: Unconstrained Portfolio Optimization with Clipping
We developed a gradient descent algorithm with momentum to solve an optimization problem that balances maximizing expected returns against penalizing large risk, measured as a powered deviation of excess returns. Key elements included:

Gradient and Momentum-Based Descent: A first-order method was implemented with an exponentially weighted moving average of gradients (momentum) to speed convergence and smooth out oscillations.

Projection via Clipping: After each gradient step, weights were clipped within [-1, 1] to enforce asset exposure constraints.

Convergence Heuristic: Instead of relying on the gradient norm (which could remain nonzero due to projection), we monitored changes in the objective value to detect convergence efficiently.

Systematic Parameter Exploration: The optimization was run for different values of risk exponent π (2, 4, 6) and a range of θ values, carefully analyzing their influence on convergence and portfolio behavior.

Task 2: Constrained Portfolio Optimization with Simplex Projection
We extended the previous setup to handle an additional set of realistic investment constraints: weights must be non-negative and sum to one. To achieve this:

Simplex Projection: We implemented a novel projection method from research literature to map arbitrary weight vectors onto the probability simplex.

Modified Gradient Descent: The same gradient and momentum logic was adapted, replacing clipping with simplex projection after each update.

Comprehensive Testing: As in Task 1, we ran systematic experiments across varying π and θ, monitoring convergence and plotting the evolution of portfolio weights.

Additional Highlights:

Data Handling: Stock data for six major companies (GOOG, TSLA, AAPL, GS, A, AAP) was downloaded using Yahoo Finance API, and both open and adjusted close prices were used to compute daily returns.

Visualization: Multiple plots illustrated the evolution of asset weights across iterations and the convergence of objective values under different parameter choices.

Heuristic Insights: Careful attention was paid to understanding why certain convergence criteria were necessary under constraints, and how momentum improved optimization stability and speed.

The project also includes a thorough understanding of all parameters used (π, θ, learning rate α, momentum β) and how they influenced both convergence behavior and final portfolio composition.


### Project 5: Stock Clustering, Return Prediction, and Constrained Portfolio Optimization

This project developed a complete pipeline for financial decision-making, involving stock clustering, predictive modeling, portfolio optimization under custom constraints, and dynamic trading strategy using dynamic programming.

The project included four major components:

Task 1: Clustering Stocks Based on Market Features

In this task, we clustered 10 major stocks into 3 groups using the following features:

Average daily returns

Variance of daily returns

Average daily trading volume

Variance of daily trading volume

Key steps included:

Feature Standardization: All features were standardized to avoid domination by high-magnitude variables like volume.

Multiple Clustering Methods: We applied both K-Means and Hierarchical Agglomerative Clustering (HAC).

Cluster Evaluation: Silhouette scores were used to select the better clustering; K-Means clustering was chosen with a higher score (0.4052 vs. 0.3748).

Final Clusters: Stocks were divided into three clusters, forming the basis for later diversification constraints in portfolio construction.

Task 2: Predicting Daily Stock Returns

We built regression models to predict next-day returns for each stock cluster.

Key highlights:

Sliding Window Cross-Validation: A rolling window was used to validate model parameters, including lag lengths, Ridge/Lasso penalties, and regularization strength.

Cluster-Based Modeling: Models were built separately for each cluster to capture internal structure among correlated stocks.

Model Selection: The best combination of lag, penalty type, and regularization coefficient was selected based on minimizing cross-validated RMSE.

Out-of-Sample Testing: The models were evaluated on data from January to June 2019, demonstrating stable prediction performance.

Task 3: Constrained Portfolio Optimization

Using predicted returns and a historical sample covariance matrix, we constructed optimal portfolios subject to real-world investment constraints.

Task 3.1: Mean-Variance Optimization with Diversification Constraints

Objective: Maximize (predicted return) minus (risk penalty), i.e., maximize r_hat^T x - lambda * x^T Sigma x.

Constraints:

Long-only: weights x_j >= 0

Fully invested: sum of weights equals 1

Diversification: total weights in each cluster ≤ 0.5

Optimization Approach: We implemented a projected gradient descent (PGD) algorithm alternating projections onto each constraint set.

Lambda Exploration: Different values of risk-aversion parameter lambda were tested to understand their impact on portfolio concentration and risk.

Task 3.2: Mean-Variance Optimization with Turnover Constraints

Additional Constraint: Turnover constraint requiring |x_j - x0_j| <= 0.1 for each stock, where x0 is the previous day's portfolio.

Modified PGD: The projected gradient descent was extended with an extra turnover projection after each update.

Alternative Approach: A penalty method was also developed as a baseline, where constraint violations were incorporated directly into the objective function, but PGD consistently achieved better optimization results.

Comparison to SciPy Solver: As a validation step, we implemented an equivalent optimization using SciPy’s minimize() function and verified the quality of our custom algorithms.

Task 4: Optimal Multi-Day Trading Strategy Using Dynamic Programming

We developed an optimal trading strategy for GS stock over an 8-day horizon, using dynamic programming techniques under trading and liquidity constraints.

Key highlights:

Problem Setup:

Initial cash balance: $100 million

Inventory bounds: 0 to 1,000,000 shares

Trading limit: no more than 0.1% of daily volume

No shorting and cash must remain non-negative.

Naive Dynamic Programming: A standard DP solution was first implemented with a complexity of O(days * max_inventory * max_volume_per_day).

Vectorized DP with Segment Tree Acceleration:

We developed a segment tree-based method to accelerate maximum queries across inventory states.

This improved the runtime to O(days * max_inventory * log(max_inventory)), making it feasible for realistic inventory sizes.

The approach avoided building enormous transition matrices by smartly querying maximum values over feasible inventory transitions.

Final Trading Strategy: The optimized trading plan produced a substantial increase in final cash balance while respecting all constraints on each day.

Overall, this project showcased a comprehensive application of machine learning, optimization, and algorithmic trading techniques in finance. We integrated clustering analysis, predictive modeling with regression, advanced constrained optimization using projected gradient methods, and dynamic programming with segment trees to design realistic, actionable trading and investment strategies.
