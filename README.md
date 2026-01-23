# Advanced Statistical Arbitrage with Reinforcement Learning

This repository implements the strategy presented in Ning & Lee (2025) – "Advanced statistical arbitrage with reinforcement learning" – combining Ornstein-Uhlenbeck modeling of mean-reverting spreads with a reinforcement learning agent for dynamic trade execution.

The core contribution is an empirical method for selecting the optimal hedge ratio β by minimizing the average reversion time from important extrema, rather than relying solely on traditional maximum likelihood estimation. Extrema are identified using the algorithm from Fink & Gandhi (2007), "Important extrema of time series."

The trading agent is trained using tabular Q-learning on discretized states of the cointegrated spread, with actions corresponding to long pair, short pair, or flat.

## Key Features

- Ornstein-Uhlenbeck process simulation via Euler–Maruyama discretization
- Empirical β optimization through grid search over reversion times from detected extrema
- Reproduction of Fink & Gandhi (2007) extrema detection algorithm with adjustable compression parameter R
- Q-learning agent trained on simulated OU paths
- Formation period (2023) used to determine optimal β; trading period (2024) for out-of-sample evaluation
- Primary pair: GOOGL – MSFT

## Results

- Sharpe ratio on simulated Ornstein-Uhlenbeck paths: ~1.85
- Positive cumulative PnL on out-of-sample backtest (2024)
- The learned policy consistently identifies profitable entry and exit points in mean-reverting regimes

## Future Directions

The current implementation uses tabular Q-learning for clarity and interpretability. Future versions will transition to deep reinforcement learning methods (e.g., DDPG, PPO, or SAC) with neural network function approximation to handle continuous state spaces and improve generalization across multiple pairs and market regimes.

## References

- Ning, Boming, and Kiseop Lee. "Advanced statistical arbitrage with reinforcement learning." International Journal of Financial Engineering 12, no. 04 (2025): 2550019.
- Fink, Eugene, and Harith Suman Gandhi. "Important extrema of time series." (2007).

Reza  
January 2026
